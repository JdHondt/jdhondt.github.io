---
title: "MULISSE: Variable-Length Similarity Search for Multivariate Time Series"
collection: publications
category: conferences
permalink: /publication/multisa25
excerpt: ''
date: 2025-05-01
venue: 'ICDE'
paperurl: /files/multisa25.pdf
---

Time series data with multiple channels, known
as multivariate time series (MTS), are increasingly common in
modern applications. A common task in this context is subse-
quence search, which involves finding subsequences within large
MTS datasets that closely match a given query pattern. While
researchers have extensively studied this problem for univariate
time series, applying these methods to multiple channels presents
key challenges, including higher dimensionality and the need for
flexible query specifications. Existing MTS search approaches
are limited - they typically only match complete time series
rather than subsequences, or restrict searches to predetermined
channel combinations. This paper introduces MULISSE, a novel
algorithm for exact variable-length k-NN subsequence search on
multivariate time series. Extending the state-of-the-art algorithm
for univariate time series (ULISSE), our approach incorporates
multivariate symbolic approximations and refined node splitting
strategies to efficiently handle multiple channels. Our experimen-
tal evaluation demonstrates the complexity of the problem: while
achieving up to two orders of magnitude speedup on synthetic
datasets with many channels, the gains over baseline methods
on real-world datasets are more modest, ranging from 10% to
2x. The method’s effectiveness is heavily influenced by factors
such as time series length, number of channels, and the index’s
hyperparameters, highlighting both the potential and current
limitations of index-based approaches for MTS search. As a first
step towards efficient variable-length MTS search, this work not
only demonstrates the viability of index-based methods but also
identifies several promising directions for future improvements
in areas such as dynamic SAX representations and cost-effective
exhaustive distance computation.