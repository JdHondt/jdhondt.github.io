---
title: "Neural downscaling of air-quality simulations requires structural correction before spatial refinement"
collection: publications
category: conferences
permalink: /publication/naturecomms_2026
excerpt: 'Preprint (under review at Nature Communications) showing that resolution-dependent model divergence, not missing spatial detail, dominates neural air-quality downscaling error — motivating structural correction before spatial refinement.'
date: 2026-08-07
venue: 'Research Square (preprint), under review at Nature Communications'
paperurl: 'https://www.researchsquare.com/article/rs-10627504/v1'
---

High-resolution air-quality information is essential for exposure assessment, operational monitoring, and mitigation design. However, producing it with Chemical Transport Models (CTMs) is computationally demanding, limiting continental forecasts to about 10 km resolution. Efficient downscaling methods are therefore needed as services such as the Copernicus Atmosphere Monitoring Service (CAMS) progress towards single-digit-kilometer grids. Existing deep-learning approaches treat the coarse field as a smoothed copy of the fine field, or learn a direct mapping without separating cross-resolution model differences from missing spatial detail. Using paired 10 and 5 km model simulations of NO2, O3, PM10, and PM2.5 over the Iberian Peninsula, we show that independently integrated resolutions produce distinct atmospheric states. This resolution-dependent model divergence, rather than missing detail, dominates the downscaling error. We decompose downscaling into structural correction on the common 10 km grid, conditioned on high-resolution forcings, followed by spatial refinement to 5 km. A probabilistic model better represents the spatial variability and distribution of structural corrections, whereas refinement is reproduced by a lightweight deterministic network preserving the corrected coarse-cell mean. Observational evaluation shows improved representation of pollution hotspots and detection of high-concentration events without increasing false alarms. These results identify cross-resolution structural correction as central to neural air-quality downscaling.
