---
title: "MS-Index: Fast Top-k Subsequence Search for Multivariate Time Series under Euclidean Distance"
seo_title: "MS-Index: Top-k Subsequence Search for Multivariate Time Series (VLDB 2026)"
collection: publications
category: conferences
permalink: /publication/msindex_2026
excerpt: 'MS-Index is an exact index for top-k subsequence search on multivariate time series under Euclidean distance, supporting ad-hoc query channel selection and outperforming the state-of-the-art by one to two orders of magnitude.'
date: 2025-10-01
venue: 'VLDB 2026 (Proceedings of the VLDB Endowment 19(2))'
authors:
  - Jens E. d'Hondt
  - Teun Kortekaas
  - Odysseas Papapetrou
  - Themis Palpanas
doi: 10.14778/3773749.3773751
paperurl: 'https://dl.acm.org/doi/10.14778/3773749.3773751'
pdfurl: '/files/msindex_vldb26_revised_camera.pdf'
citation: "Jens E. d'Hondt, Teun Kortekaas, Odysseas Papapetrou, and Themis Palpanas. 2025. MS-Index: Fast Top-k Subsequence Search for Multivariate Time Series under Euclidean Distance. Proc. VLDB Endow. 19, 2, 99–112."
---

Modern applications frequently collect and analyze temporal data in the form of multivariate time series (MTS) - time series that contain multiple channels. A common task in this context is subsequence search, which involves identifying all MTS that contain subsequences highly similar to a query time series. In practical scenarios, not all channels of an MTS are relevant to every query. For instance, airplane sensors may gather data on a plethora of components and subsystems, but only a few of these are relevant to a specific query, such as identifying the cause of a malfunctioning landing gear, or a specific flight maneuver. Consequently, the relevant query channels are often specified at query time. In this work, we introduce the Multivariate Subsequence Index (MS-Index), a novel algorithm for nearest neighbor MTS subsequence search under Euclidean distance that supports ad-hoc selection of query channels. The algorithm is exact and demonstrates query performance that scales sublinearly to the number of query channels. We examine the properties of MS-Index with a thorough experimental evaluation over 34 datasets, and show that it outperforms the state-of-the-art one to two orders of magnitude for both raw and normalized subsequences.

**Resources:** [camera-ready PDF](/files/msindex_vldb26_revised_camera.pdf), [arXiv preprint](https://arxiv.org/abs/2512.14723), [source code on GitHub](https://github.com/JdHondt/MS-Index) (Java). The paper will be presented at VLDB 2026 in Boston. Our earlier, variable-length approach to the same problem is [MULISSE](/publication/multisa25).
