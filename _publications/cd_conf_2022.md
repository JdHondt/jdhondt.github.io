---
title: "Multivariate correlations discovery in static and streaming data"
seo_title: "Multivariate Correlations Discovery (VLDB 2022)"
collection: publications
category: conferences
permalink: /publication/cd_conf_2022
header:
  teaser: papers/cd_conf_2022.png
excerpt: 'VLDB 2022 paper introducing efficient algorithms (Correlation Detective) for discovering strong multivariate correlations in static and streaming data, outperforming the state-of-the-art typically by an order of magnitude.'
date: 2022-02-01
venue: 'VLDB 2022 (Proceedings of the VLDB Endowment 15(6))'
authors:
  - Koen Minartz
  - Jens E. d'Hondt
  - Odysseas Papapetrou
doi: 10.14778/3514061.3514072
slidesurl: '/files/vldb22_10min.pptx'
paperurl: 'https://www.vldb.org/pvldb/vol15/p1266-papapetrou.pdf'
citation: "Koen Minartz, Jens E. d'Hondt, and Odysseas Papapetrou. 2022. Multivariate correlations discovery in static and streaming data. Proc. VLDB Endow. 15, 6 (February 2022), 1266–1278."
---

Correlation analysis is an invaluable tool in many domains, for better understanding data and extracting salient insights. Most works to date focus on detecting high pairwise correlations. A generalization of this problem with known applications but no known efficient solutions involves the discovery of strong multivariate correlations, i.e., finding vectors (typically in the order of 3 to 5 vectors) that exhibit a strong dependence when considered altogether. In this work we propose algorithms for detecting multivariate correlations in static and streaming data. Our algorithms, which rely on novel theoretical results, support two different correlation measures, and allow for additional constraints. Our extensive experimental evaluation examines the properties of our solution and demonstrates that our algorithms outperform the state-of-the-art, typically by an order of magnitude.

<figure>
  <a href="/images/papers/cd_conf_2022.png" target="_blank" rel="noopener"><img src="/images/papers/cd_conf_2022.png" alt="Hierarchical clustering of eight time series a to h: a root cluster containing all of them, split into clusters C1, C2 and C3, which are split further into clusters C4 to C10." style="width:75%;display:block;margin:0 auto"></a>
  <figcaption>The running example: time series are organised in a hierarchy of clusters, so that bounds on the correlation of whole cluster combinations can rule out or confirm many candidate correlations at once. (Figure from the paper; click to enlarge.)</figcaption>
</figure>

The algorithms are available as the open-source [Correlation Detective](https://correlationdetective.com/) library. An extended version supporting four correlation measures appeared in the [VLDB Journal](/publication/cd_journal_2024). I presented this work at [VLDB 2022 in Sydney](/talks/2022-09-09-cd-vldb).
