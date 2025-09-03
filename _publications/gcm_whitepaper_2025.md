---
title: "Generative Correlation Manifolds: Generating Synthetic Data with Preserved Higher-Order Correlations"
collection: publications
category: conferences
permalink: /publication/gcm_whitepaper_2025
excerpt: ''
date: 2025-09-03
venue: 'Arxiv'
paperurl: '/files/gcm_whitepaper.pdf'
---

The increasing need for data privacy and the demand for robust machine learning models have fueled the development of synthetic data generation techniques. However, current methods often succeed in replicating simple summary statistics but fail to preserve both the pairwise and higher-order correlation structure of the data that define the complex, multi-variable interactions inherent in real-world systems. This limitation can lead to synthetic data that is superficially realistic but fails when used for sophisticated modeling tasks. In this white paper, we introduce Generative Correlation Manifolds (GCM), a computationally efficient method for generating synthetic data. The technique uses Cholesky decomposition of a target correlation matrix to produce datasets that, by mathematical proof, preserve the entire correlation structure – from simple pairwise relationships to higher-order interactions – of a z-normalized source dataset. We argue that this method provides a new approach to synthetic data generation with potential applications in privacy-preserving data sharing, robust model training,
and simulation.