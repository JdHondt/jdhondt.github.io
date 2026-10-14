---
title: "Effective and Efficient Multivariate Similarity Search: Uncovering the Hidden Relationships in Modern Datasets"
seo_title: "Effective and Efficient Multivariate Similarity Search (PhD thesis, TU Eindhoven)"
collection: publications
category: theses
permalink: /publication/phd_thesis_2025
header:
  teaser: papers/phd_thesis_2025.png
excerpt: 'PhD thesis (TU Eindhoven, 2025) extending similarity search beyond univariate, pairwise comparisons: distance measures and fast subsequence search for multivariate time series, and exact algorithms for finding correlations among three or more variables.'
date: 2025-12-16
venue: 'PhD thesis, Eindhoven University of Technology'
institution: 'Eindhoven University of Technology'
isbn: '978-90-386-6562-7'
authors:
  - Jens E. d'Hondt
paperurl: '/files/phd_thesis_2025.pdf'
citation: "Jens E. d'Hondt. 2025. Effective and Efficient Multivariate Similarity Search: Uncovering the Hidden Relationships in Modern Datasets. PhD thesis, Eindhoven University of Technology. SIKS Dissertation Series No. 2025-64. ISBN 978-90-386-6562-7."
---

<a href="/files/phd_thesis_2025.pdf" target="_blank" rel="noopener"><img src="/images/papers/phd_thesis_2025_cover.jpg" alt="Thesis cover: dark blue background with a white network of connected dots at the top, the title Effective and Efficient Multivariate Similarity Search, and glowing contour plots around red centres scattered over a grid of dots." style="float:right; width:40%; max-width:200px; margin:0 0 1em 1.5em;"></a>

Similarity search, given an object or pattern of interest, find the most similar objects in a dataset, is one of the basic operations of data analysis. For decades it has mostly been studied in a simple setting: each object is measured through a single variable, and similarity is measured between two objects at a time. Modern datasets are rarely like that. Sensors record many variables at once, and many phenomena, from brain activity to weather, are driven by interactions between more than two variables.

This dissertation extends similarity search in two directions. The **data-level extension** (Part I) compares objects that are themselves multivariate, such as a weather station recording temperature, wind and precipitation together. The **relation-level extension** (Part II) looks for relationships that only appear when three or more variables are considered together. For both, it asks what makes the search *effective* (the right notion of similarity) and *efficient* (fast enough to run on large data).

I defended the thesis at TU Eindhoven on 16 December 2025. Promotor: prof. dr. George Fletcher; co-promotor: dr. Odysseas Papapetrou. Committee: prof. dr. Mark de Berg (chair), dr. Vlado Menkovski, prof. dr. Felix Naumann (Hasso Plattner Institute), prof. dr. Torben Bach Pedersen (Aalborg University) and prof. dr. Yannis Velegrakis (Utrecht University).

**Resources:** [full thesis PDF](/files/phd_thesis_2025.pdf) (284 pages), [record in the TU/e research portal](https://research.tue.nl/en/publications/effective-and-efficient-multivariate-similarity-search-uncovering/).

<figure>
  <a href="/images/papers/phd_thesis_2025.png" target="_blank" rel="noopener"><img src="/images/papers/phd_thesis_2025.png" alt="Two maps of Europe with weather stations in Amsterdam, Moscow and Rome. Left, data-level extension: each station holds several time series (temperature, wind, precipitation) and arrows between pairs of stations carry similarity scores 0.2, 0.4 and 0.7. Right, relation-level extension: each station holds one temperature series and a single circular arrow joins all three with one similarity score of 0.5." style="width:100%"></a>
  <figcaption>The two extensions studied in the thesis, with weather stations as the example. Left: pairwise similarity between multivariate time series. Right: one combined similarity score for a group of three univariate time series. (Figure 1.1 of the thesis; click to enlarge.)</figcaption>
</figure>

## Chapter by chapter

**Chapters 1 and 2: Introduction and foundations.** The problem statement, the central research question (can similarity search be extended to the multivariate setting, and does that reveal better patterns?), and the formal definitions, approximation methods and index structures used in the rest of the thesis.

<figure class="compact">
  <a href="/images/papers/thesis/ch2_dft.png" target="_blank" rel="noopener"><img src="/images/papers/thesis/ch2_dft.png" alt="A wavy time series in the time domain on the left, an arrow labelled DFT, and on the right a bar chart of frequency magnitudes where the first few bars are large and the rest near zero." loading="lazy"></a>
  <figcaption>Figure 2.2: the Discrete Fourier Transform summarises a time series with a few coefficients, the basis of several indexes in the thesis.</figcaption>
</figure>


### Part I: Pairwise similarity search on multivariate time series

**Chapter 3: A structured study of distance measures for multivariate time series.** Which distance measure should you use to compare multivariate time series? The chapter organises measures along three axes (normalisation, temporal model, and how channels are combined) and benchmarks 30 measures with 13 normalisation methods on 30 datasets, for classification, clustering and anomaly detection. Main findings: SBD-D gives the best accuracy-to-runtime trade-off, no existing normalisation beats not normalising at all, and handling channels independently only pays off for elastic measures such as DTW.

<figure class="compact">
  <a href="/images/papers/thesis/ch3_measures.png" target="_blank" rel="noopener"><img src="/images/papers/thesis/ch3_measures.png" alt="Seven panels, one per temporal model of distance measures: lock-step (one-to-one point matching), sliding (shifting one series against the other), elastic (one-to-many alignment), kernel (mapping into a feature space via a kernel function), feature-based (comparing extracted features), model-based (comparing fitted model parameters), and embedding (comparing learned embeddings)." loading="lazy"></a>
  <figcaption>Figure 3.2: the seven temporal models behind the distance measures in the study, from lock-step and elastic matching to model-based comparison and learned embeddings. (Figure by Fan Yang.)</figcaption>
</figure>

Based on: [A Structured Study of Multivariate Time-Series Distance Measures](/publication/sigmod_2025) (SIGMOD 2025), [Beyond the Dimensions](/publication/icde_jens_talk) (ICDE 2024 workshops) and [A Survey on Time-Series Distance Measures](/publication/book_chapter_2024). Practical summary: [blog post on choosing a distance measure](/blog/distance-measures-multivariate-time-series/).

**Chapter 4: Efficient subsequence search in multivariate time series.** MS-Index finds the k most similar subsequences in a collection of multivariate time series, exactly, and lets the user pick which channels matter at query time. Over 34 datasets it is one to two orders of magnitude faster than the state of the art, with speedups up to 1000x.

<figure class="compact">
  <a href="/images/blog/ms-index/problem.png" target="_blank" rel="noopener"><img src="/images/blog/ms-index/problem.png" alt="Four channels of flight data: altitude, landing gear, engine temperature and latitude. A short query window of a failed landing on the left; a long historical record on the right with the best-matching window highlighted on the altitude and landing gear channels only. Engine temperature and latitude are greyed out and marked ignored." loading="lazy"></a>
  <figcaption>Ad-hoc channel selection, the problem MS-Index solves: only altitude and landing gear matter for this query. (Illustration from the MS-Index page.)</figcaption>
</figure>

Based on: [MS-Index](/publication/msindex_2026) (VLDB 2026) and [MULISSE](/publication/multisa25) (ICDE 2025 workshops). Practical summary: [blog post on MS-Index](/blog/ms-index-multivariate-subsequence-search/).

### Part II: Multivariate similarity search on univariate data

**Chapter 5: Efficient detection of multivariate correlations.** Correlation Detective (CD) finds groups of three or more time series that are strongly correlated together, a search space that grows combinatorially with the group size. CD clusters the series and computes bounds on combinations of clusters, so most candidate groups are pruned without being evaluated. CDStream maintains the results over sliding windows on streaming data, and CDHybrid switches between the two. Compared with the original algorithm, the improvements in this chapter speed up queries on static data by up to 77x and add support for non-synchronised streams.

Based on: [Efficient detection of multivariate correlations with different correlation measures](/publication/cd_journal_2024) (VLDB Journal) and [Multivariate correlations discovery in static and streaming data](/publication/cd_conf_2022) (VLDB 2022). Software: [Correlation Detective](https://correlationdetective.com/).

**Chapter 6: Towards a general multivariate similarity search framework.** Many fields search for high-order relationships, each with its own measures and tools. The Similarity Detective (SD) framework generalises CD to any multivariate similarity measure: the user implements a small measure interface, and the framework picks which bounds and optimisations apply from the formal properties of that measure.

Based in part on the [VLDB Journal article](/publication/cd_journal_2024), and following up on our ICDE 2024 [call for multivariate similarity search algorithms](/publication/icde_ody_talk).

**Chapter 7: Case study, sparse representation.** Sparse representation (approximating a signal with as few dictionary atoms as possible) can be phrased as a multivariate similarity search query. Without domain-specific tuning, SD is competitive with established methods such as OMP on reconstruction error, sparsity, classification accuracy and runtime, and finds the optimal solution on adversarial examples where greedy methods fail. This chapter has not been published elsewhere.

<figure class="compact">
  <a href="/images/papers/thesis/ch7_twinsine.png" target="_blank" rel="noopener"><img src="/images/papers/thesis/ch7_twinsine.png" alt="Three panels: a signal made of two close sinusoids, the coefficients picked by OMP, concentrated on a single frequency between the two true ones, and the coefficients from basis pursuit denoising, which recover both." loading="lazy"></a>
  <figcaption>Figure 7.1: the TwinSine signal, two nearly identical sinusoids. The greedy OMP algorithm typically picks only one of them.</figcaption>
</figure>


**Chapter 8: Conclusions and future directions.** The open "grand challenge" is to combine both extensions: searching for relationships among groups of objects that are themselves multivariate. The chapter outlines what that requires, both in defining and evaluating such measures and in making the search tractable.
