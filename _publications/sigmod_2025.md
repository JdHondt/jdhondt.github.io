---
title: "A Structured Study of Multivariate Time-Series Distance Measures"
collection: publications
category: conferences
permalink: /publication/sigmod_2025
excerpt: ''
date: 2025-06-23
venue: 'SIGMOD'
paperurl: 'https://dl.acm.org/doi/10.1145/3725258'
---

Distance measures are fundamental to time series analysis and have been extensively studied for decades.
Until now, research efforts mainly focused on univariate time series, leaving multivariate cases largely under-
explored. Furthermore, the existing experimental studies on multivariate distances have critical limitations: (a)
focusing only on lock-step and elastic measures while ignoring categories such as sliding and kernel measures;
(b) considering only one normalization technique; and (c) placing limited focus on statistical analysis of findings.
Motivated by these shortcomings, we present the most complete evaluation of multivariate distance measures
to date. Our study examines 30 standalone measures across 8 categories, 2 channel-dependency models, and
considers 13 normalizations. We perform a comprehensive evaluation across 30 datasets and 3 downstream
tasks, accompanied by rigorous statistical analysis. To ensure fairness, we conduct a thorough investigation of
parameters for methods in both a supervised and an unsupervised manner. Our work verifies and extends
earlier findings, showing that insights from univariate distance measures also apply to the multivariate case:
(a) alternative normalization methods outperform Z-score, and for the first time, we demonstrate statistical
differences in certain categories for the multivariate case; (b) multiple lock-step measures are better suited than
Euclidean distance, when it comes to multivariate time series; and (c) newer elastic measures outperform the
widely adopted Dynamic Time Warping distance, especially with proper parameter tuning in the supervised
setting. Moreover, our results reveal that (a) sliding measures offer the best trade-off between accuracy and
runtime; (b) current normalization techniques fail to significantly enhance accuracy on multivariate time series
and, surprisingly, do not outperform the no normalization case, indicating a lack of appropriate solutions for
normalizing multivariate time series; and (c) independent consideration of time series channels is beneficial
only for elastic measures. In summary, we offer guidelines to aid in designing and selecting preprocessing
strategies and multivariate distance measures for our community.