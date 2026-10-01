---
title: "Searching multivariate time series when only some channels matter"
date: 2026-10-01
permalink: /blog/ms-index-multivariate-subsequence-search/
header:
  teaser: blog/ms-index/problem.png
excerpt: "How MS-Index finds top-k similar subsequences in multivariate time series when the relevant channels are only chosen at query time, exactly and fast."
tags:
  - time series
  - similarity search
  - indexing
---

**TL;DR.** MS-Index is an exact index for top-k subsequence search on multivariate time series under Euclidean distance, and it lets you pick which channels the query should look at when you run the query, not when you build the index. It summarises every subsequence with a handful of data-adapted DFT coefficients per channel, stores those in one R-tree, and uses two probes of the tree plus MASS to prune over 99% of candidates while still returning the correct answer. Across 34 datasets it was one to two orders of magnitude faster than the state of the art, for both raw and normalised subsequences, and its query time grows sublinearly with the number of query channels.

## The problem

Most sensor data these days is multivariate: many channels recorded together about the same object. An airplane logs altitude, latitude, landing gear state, engine parameters, and much more. Suppose an engineer is investigating a failed landing they suspect was caused by the landing gear. They take the short window of the failed landing and ask: where in our historical data did something similar happen?

That is a **subsequence search** query: given a query pattern of some length, find the k windows of the same length, anywhere in a large collection of long time series, that look most like it. The catch is which channels count. For the landing gear question, altitude and landing gear matter and engine temperature does not. For a question about a manoeuvre, a different set matters. The channel set is a property of the *question*, so it is only known at query time. In the paper we call this **ad-hoc channel selection**.

<figure>
  <a href="/images/blog/ms-index/problem.png" target="_blank" rel="noopener"><img src="/images/blog/ms-index/problem.png" alt="Four channels of flight data: altitude, landing gear, engine temperature and latitude. A short query window of a failed landing on the left; a long historical record on the right with the best-matching window highlighted on the altitude and landing gear channels only. Engine temperature and latitude are greyed out and marked ignored." style="width:100%"></a>
  <figcaption>Ad-hoc channel selection. The engineer picks the window of a failed landing and decides, for this question, that only altitude and landing gear count. The best match in the historical data is the window closest on those two channels; engine temperature and latitude play no part. Another question would pick other channels, against the same index. (Illustration with synthetic data; click to enlarge.)</figcaption>
</figure>

Existing work does not cover this. Univariate indexes (ST-index, KV-match, DSTree, iSAX) handle one channel. The few multivariate indexes either match whole time series rather than subsequences, bake a fixed channel set into the index, or need a distance threshold per channel, which is not what a k-NN query looks like. You can glue per-channel univariate indexes together with a threshold-algorithm wrapper (we did, for baselines), but its pruning power turns out to be poor.

## How MS-Index works

MS-Index has three pieces: a summary of every subsequence, an R-tree over those summaries, and a two-pass query that uses MASS for exact distances. None is new on its own. What is new is combining them so that the result works over any subset of channels, stays exact, and gets faster rather than slower as you add channels.

<figure>
  <a href="/images/blog/ms-index/summarization.png" target="_blank" rel="noopener"><img src="/images/blog/ms-index/summarization.png" alt="Diagram of the MS-Index pipeline: each channel of a multivariate time series is approximated with a few Fourier coefficients, the coefficients are flattened into one feature vector, and the vectors are stored in an R-tree whose leaves group time-neighbouring subsequences." style="width:100%"></a>
  <figcaption>Summarising and indexing. Every subsequence is reduced to a few DFT coefficients per channel, flattened into one feature vector, and stored in a single R-tree where time-neighbouring subsequences share an entry. (Figure from the paper; click to enlarge.)</figcaption>
</figure>

**Summarising subsequences with the right DFT coefficients.** The standard trick for Euclidean distance is to take the discrete Fourier transform and keep only a few coefficients; the distance between two truncated DFTs is a lower bound on the true distance, so it can be used to prune. The usual choice is the first f coefficients, since low frequencies carry most of the energy. Real data disagreed with that on two counts. The highest-energy coefficients are not always the first ones (a temperature dataset had a jump at the 62nd coefficient, from the daily cycle). And the coefficients that matter for *distances between* series are more concentrated than the ones that carry energy: on that dataset the top 5 coefficients covered about 90% of the distance but only about 60% of the energy. So MS-Index takes a sample of subsequences (typically 100), measures how much each coefficient of each channel contributes to pairwise distances, and keeps the top coefficients per channel until a target share of the distance is covered (60% worked best). These are flattened into one feature vector of length channels times f.

<figure>
  <img src="/images/blog/ms-index/coefficients.png" alt="Two stacked line charts over DFT coefficient index on a temperature channel. Top: absolute share of total distance and energy per coefficient. Bottom: cumulative share. Distance is concentrated in fewer coefficients than energy, with a second spike near coefficient 62." style="width:55%;display:block;margin:0 auto">
  <figcaption>Distance versus energy across DFT coefficients on a temperature channel. A handful of coefficients cover most of the distance, but not most of the energy, and the important ones are not simply the first few (note the jump near coefficient 62, the daily cycle). (Figure from the paper.)</figcaption>
</figure>

**One R-tree, with neighbouring windows grouped.** All feature vectors go into a single R-tree, built bottom-up. A series of length m has about m subsequences, so the naive entry count is huge, but consecutive windows overlap almost entirely and land close together in feature space. After building the leaves, MS-Index merges runs of time-neighbouring subsequences from the same series into one entry: a bounding rectangle plus a start and end offset. That merges around 8 to 50 subsequences per entry, and lets one lower-bound computation prune a whole run of windows at once.

**Arbitrary channel subsets.** This is almost free, and it is why there is one tree rather than one per channel. The DFT lower bound holds for any subset of coefficients, so dropping the dimensions of channels you do not care about keeps it valid. An R-tree can answer a query on a subset of its dimensions natively, so at query time we project the query onto the dimensions of the chosen channels and search. The index never needs to know in advance which channels will be asked for.

**Staying exact with two probes.** The first probe is a best-first search for the k entries with the smallest lower bound, followed by exact distances with MASS (the convolution-based algorithm that gives the distance from the query to every window of a series in O(m log m)). The k-th smallest exact distance becomes a threshold. The second probe is a range query with that threshold, again followed by exact MASS distances. Since every lower bound sits below the true distance, no true neighbour can fall outside the range, so the result is exact (Lemma 3.1 in the paper). Three tweaks sharpen the pruning: a pivot-based correction term for the distance the kept coefficients miss (about 2x faster queries), variance-weighted R-tree partitioning (1.5 to 3x), and distance browsing so the second probe continues where the first stopped. Combined, about a factor of 4.

<figure>
  <a href="/images/blog/ms-index/querying.png" target="_blank" rel="noopener"><img src="/images/blog/ms-index/querying.png" alt="Four-step diagram of a 1-NN query: best-first search of the R-tree for an initial candidate, exact MASS distances on the raw data, a threshold query using the best distance found, and a final MASS pass to return the exact nearest neighbour." style="width:100%"></a>
  <figcaption>Answering a 1-NN query in two probes. A best-first search gives an initial candidate, whose exact distance becomes the threshold; a second range query with that threshold collects every window that could still be closer, and exact distances on those give the answer. (Figure from the paper; click to enlarge.)</figcaption>
</figure>

**Why more channels makes it faster.** Each added channel adds a few dimensions, which costs a little per node visited, but it also makes the lower bounds more discriminative. On the 1024-channel DuckDuckGeese dataset, going from 8 to 16 query channels cut query time from 8.4 to 4.4 ms, and it grew only slowly after that. The share of R-tree nodes pruned rose from 70.5% at 16 channels to 97.9% at 1024 (raw subsequences). The per-channel baselines grow almost linearly, because they union per-channel results.

## What the experiments showed

We ran on 34 datasets: Stocks (28,678 stocks, 5 channels, query length 730 days), Weather (13,545 sensors, 4 channels), Wind (one 432,000-point turbine series, 10 channels), a 64-channel synthetic set, and the 30 UEA archive datasets. Baselines were MULISSE (our earlier multivariate index), MASS, brute force, and multivariate wrappers of ST-index, KV-match and DSTree. All single-threaded, in memory, Java 11.

<figure>
  <a href="/images/blog/ms-index/query-time.png" target="_blank" rel="noopener"><img src="/images/blog/ms-index/query-time.png" alt="Bar chart of average query time in seconds on a log scale for seven algorithms on the Stocks, Weather, Synthetic, Wind and UEA datasets with raw subsequences. MS-Index, the last bar in each group, is the lowest in all five." style="width:100%"></a>
  <img src="/images/blog/ms-index/query-time-legend.png" alt="Legend: brute force, MASS, DSTree, ST-index, KV-match, MULISSE, MS-Index" style="width:90%;margin-top:.5em">
  <figcaption>Average query time per dataset (raw subsequences, log scale, bars in the order of the legend). MS-Index is the rightmost bar in each group. (Figure from the paper; click to enlarge.)</figcaption>
</figure>

| Setting | Closest competitor | MS-Index speedup |
|---|---|---|
| Stocks, raw, all channels | MASS | over 100x (over 1000x vs the other indexes) |
| Wind, raw (very long series) | MASS | about 22x (about 100x vs the others) |
| 30 UEA datasets, raw | MASS | 5 to 7x |
| Weather and Synthetic, raw | MASS or DSTree | 1 to 2 orders of magnitude |
| Normalised subsequences | MASS | "similar patterns" to raw per the paper; pruning weakens slowly as channels grow |

Median pruning was 99% of subsequences. The per-channel wrappers pruned only 52% (ST-index), 65% (KV-match) and 46% (DSTree) on Stocks, and MULISSE 9%. Query time is independent of query length, since MASS's cost depends on the series length, not the query.

## When to use it, and when not to

Use MS-Index if you run many k-NN subsequence queries against a fixed collection, need exact results under Euclidean distance, and want to choose channels per query. Raw and z-normalised subsequences both work.

Think twice if:

- **Your query length changes.** MS-Index is fixed-length: the query length is a build parameter. For variable lengths, see MULISSE.
- **You run only a handful of queries.** Index construction costs about as much as ST-index (both spend the time on DFTs). On Stocks, MS-Index only beats plain MASS on total cost after about 45 queries.
- **Memory is tight.** The index summarises every subsequence. On Stocks with 2,000 series (430 MB), the raw index was 1,923 MB, about 4.5x the data; normalised 5.2x. MULISSE, at 5%, is far smaller and pays for it in query time.
- **Your queries are far from the data.** For noisy or out-of-distribution queries, the contrast between near and far windows shrinks, pruning collapses, and MS-Index degrades to roughly MASS plus tree overhead. Use a sequential scan there. A hybrid that picks by estimated query difficulty is future work.
- **You want DTW.** Euclidean only.

## Running it

The repository is Java with Maven. There is no library API; everything is driven from `run.sh`. Build the jar first (the script expects `target/MS-Index-1.0-jar-with-dependencies.jar`):

```bash
git clone https://github.com/JdHondt/MS-Index.git
cd MS-Index
mvn clean package
```

Then edit the variables at the top of `run.sh` and run it:

```bash
algorithmType=MSINDEX     # or BRUTE_FORCE, MASS, ST_INDEX, DSTREE, KV_MATCH
dataPath=data/synthetic   # see data/instructions.md for the paper's datasets
N=100                     # number of time series to load
channels=-1               # channels per series, -1 = all
nQueryChannels=-1         # channels used in the query, -1 = all
qLen=730                  # query (and index) subsequence length
K=1                       # neighbours to return
normalize=false           # z-normalised subsequences
nQueries=100
runtimeMode=FULL_NO_STORE # FULL, INDEX, QUERY variants

./run.sh
```

## Links

- Paper page on this site: [MS-Index](/publication/msindex_2026)
- The earlier workshop paper on variable-length search: [MULISSE](/publication/multisa25)
- arXiv: [2512.14723](https://arxiv.org/abs/2512.14723)
- Code: [github.com/JdHondt/MS-Index](https://github.com/JdHondt/MS-Index) (MIT licence)

## Cite this

{% raw %}
```bibtex
@article{dhondt2025msindex,
  author  = {d'Hondt, Jens and Kortekaas, Teun and Papapetrou, Odysseas and Palpanas, Themis},
  title   = {{MS-Index}: Fast Top-k Subsequence Search for Multivariate Time Series under {Euclidean} Distance},
  journal = {Proceedings of the VLDB Endowment},
  volume  = {19},
  number  = {2},
  pages   = {99--112},
  year    = {2025},
  doi     = {10.14778/3773749.3773751}
}
```
{% endraw %}
