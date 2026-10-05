---
title: "Multivariate Similarity Search - A Call for a New Breed of Similarity Search Algorithms"
seo_title: "Multivariate Similarity Search: A Call for New Algorithms (ICDE 2024)"
collection: publications
category: conferences
permalink: /publication/icde_ody_talk
header:
  teaser: papers/icde_ody_talk.png
excerpt: 'ICDE 2024 talk revisiting similarity search under the lens of multivariate similarity measures, calling for a new breed of similarity search algorithms.'
date: 2024-05-13
venue: 'ICDE 2024'
authors:
  - Odysseas Papapetrou
  - Jens E. d'Hondt
doi: 10.1109/ICDE60146.2024.00461
paperurl: 'https://ieeexplore.ieee.org/document/10597715'
citation: "O. Papapetrou and J. E. d'Hondt, \"Multivariate Similarity Search - A Call for a New Breed of Similarity Search Algorithms,\" 2024 IEEE 40th International Conference on Data Engineering (ICDE), Utrecht, Netherlands, 2024, pp. 5662-5662."
---

The similarity search task involves identifying pairs of similar vectors, e.g., time series. For example, given a query q, the user might wish to find all vectors in a dataset with a cosine similarity with q higher than a threshold t, or to find the top-k most similar vectors with q, using Euclidean distance. The task has been widely considered in different domains, ranging from data science for detecting correlations that help the analyst extract insights from the data, to e-commerce for recommending additional purchases to the users based on their shopping behavior. Accordingly, many similarity search algorithms and indices were proposed in the literature, focusing on efficiency, scalability for big datasets, and different distance measures. However, the majority of past work only considers pairwise similarity/distance measures. In this talk we will revisit similarity search under the lens of multivariate similarity measures.

<figure>
  <a href="/images/papers/icde_ody_talk.png" target="_blank" rel="noopener"><img src="/images/papers/icde_ody_talk.png" alt="Line chart of z-normalized daily closing prices over ten days for the stocks MCP, QAN and RDF, plus the average of QAN and RDF, which closely tracks MCP." style="width:65%;display:block;margin:0 auto"></a>
  <figcaption>A multivariate similarity. QAN and RDF are not strongly correlated with MCP on their own, but their average follows MCP closely. Pairwise similarity search cannot find this. (Figure from the paper, originally from our VLDB Journal article.)</figcaption>
</figure>

The algorithms this talk calls for are the subject of my PhD thesis. See [Correlation Detective](/publication/cd_conf_2022) for multivariate correlation discovery and [MS-Index](/publication/msindex_2026) for multivariate subsequence search.
