---
title: "Generative Correlation Manifolds: Generating Synthetic Data with Preserved Higher-Order Correlations"
seo_title: "Generative Correlation Manifolds: Synthetic Data with Preserved Correlations"
collection: publications
category: preprints
permalink: /publication/gcm_whitepaper_2025
excerpt: 'White paper introducing Generative Correlation Manifolds (GCM), a computationally efficient synthetic data generation method that provably preserves the full correlation structure of a source dataset, from pairwise to higher-order interactions.'
date: 2025-09-03
venue: 'arXiv'
authors:
  - Jens E. d'Hondt
  - Wieger R. Punter
  - Odysseas Papapetrou
doi: 10.48550/arXiv.2510.21610
paperurl: 'https://arxiv.org/abs/2510.21610'
pdfurl: '/files/gcm_whitepaper.pdf'
citation: "d'Hondt, J.E., Punter, W.R., Papapetrou, O. (2025). Generative Correlation Manifolds: Generating Synthetic Data with Preserved Higher-Order Correlations. arXiv preprint arXiv:2510.21610."
---

The increasing need for data privacy and the demand for robust machine learning models have fueled the development of synthetic data generation techniques. However, current methods often succeed in replicating simple summary statistics but fail to preserve both the pairwise and higher-order correlation structure of the data that define the complex, multi-variable interactions inherent in real-world systems. This limitation can lead to synthetic data that is superficially realistic but fails when used for sophisticated modeling tasks. In this white paper, we introduce Generative Correlation Manifolds (GCM), a computationally efficient method for generating synthetic data. The technique uses Cholesky decomposition of a target correlation matrix to produce datasets that, by mathematical proof, preserve the entire correlation structure – from simple pairwise relationships to higher-order interactions – of a z-normalized source dataset. We argue that this method provides a new approach to synthetic data generation with potential applications in privacy-preserving data sharing, robust model training, and simulation.

**Resources:** [arXiv](https://arxiv.org/abs/2510.21610), [PDF](/files/gcm_whitepaper.pdf), [code on GitHub](https://github.com/JdHondt/gcm). The higher-order correlations GCM preserves are the same ones [Correlation Detective](/publication/cd_journal_2024) searches for.
