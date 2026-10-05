---
title: "Efficient detection of multivariate correlations with different correlation measures"
seo_title: "Efficient Detection of Multivariate Correlations (VLDB Journal)"
collection: publications
category: manuscripts
permalink: /publication/cd_journal_2024
header:
  teaser: papers/cd_journal_2024.png
excerpt: 'VLDB Journal article on efficient detection of multivariate correlations, supporting four different correlation measures and additional constraints for static and streaming data.'
date: 2023-10-11
venue: 'The VLDB Journal'
authors:
  - Jens E. d'Hondt
  - Koen Minartz
  - Odysseas Papapetrou
doi: 10.1007/s00778-023-00815-y
paperurl: 'https://link.springer.com/article/10.1007/s00778-023-00815-y'
citation: "d'Hondt, J.E., Minartz, K. & Papapetrou, O. Efficient detection of multivariate correlations with different correlation measures. The VLDB Journal 33, 481–505 (2024)."
---

Correlation analysis is an invaluable tool in many domains, for better understanding the data and extracting salient insights. Most works to date focus on detecting high pairwise correlations. A generalization of this problem with known applications but no known efficient solutions involves the discovery of strong multivariate correlations, i.e., finding vectors (typically in the order of 3–5 vectors) that exhibit a strong dependence when considered altogether. In this work, we propose algorithms for detecting multivariate correlations in static and streaming data. Our algorithms, which rely on novel theoretical results, support four different correlation measures, and allow for additional constraints. Our extensive experimental evaluation examines the properties of our solution and demonstrates that our algorithms outperform the state-of-the-art, typically by an order of magnitude.

<figure>
  <a href="/images/papers/cd_journal_2024.png" target="_blank" rel="noopener"><img src="/images/papers/cd_journal_2024.png" alt="Index structure with one column per time series (a, b, c). Each column lists pairs of series and their cluster combinations, with decisive positive and negative combinations marked by green and red dots that point to the cluster combinations they affect." style="width:100%"></a>
  <figcaption>The decisive combination index used by CDStream, the streaming algorithm. For every time series it records which cluster combinations are decisive, so that when new data arrives only the affected combinations have to be re-evaluated. (Figure from the paper; click to enlarge.)</figcaption>
</figure>

This article extends our [VLDB 2022 paper](/publication/cd_conf_2022) from two to four correlation measures. The implementation is part of the [Correlation Detective](https://correlationdetective.com/) library, and I discussed the different measures in a [DSDSD seminar talk](/talks/2023-03-24-dsdsd).
