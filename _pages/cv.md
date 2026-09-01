---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

A PDF version of my CV is available [here]({{ base_path }}/files/postdoc25.pdf).

Education
======
* Ph.D. in Computer Science, Eindhoven University of Technology (TU/e), Nov 2021 – Dec 2025
  * Thesis: *Efficient Algorithms for Multivariate Similarity Search*
  * Supervisors: dr. Odysseas Papapetrou and prof. dr. George Fletcher
* M.Sc. in Data Science and Artificial Intelligence, TU/e, 2019 – 2021 — *Cum Laude* (GPA 9.1/10)
* B.Sc. in Industrial Engineering, TU/e, 2016 – 2019 — *Cum Laude* (GPA 8.5/10)

Work experience
======
* Dec 2025 – present: Postdoctoral Scientist
  * Barcelona Supercomputing Center (BSC), Earth Sciences Department
  * Developing generative AI methods for downscaling atmospheric chemistry simulations — diffusion models, flow-matching, and physics-constrained CNNs with hard constraints such as mass conservation

* Nov 2021 – Dec 2025: Doctoral Researcher
  * Eindhoven University of Technology, Data & AI cluster
  * Scalable multivariate time-series similarity search algorithms; published at VLDB, VLDB Journal, SIGMOD, and ICDE
  * Led work in the EU-funded STELAR project on ML pipelines for agricultural field delineation from satellite imagery

* Dec 2019 – Nov 2021: Freelance Software Engineer
  * Data-driven applications and statistical analyses for clients (Python, Spark, Kafka, TensorFlow, AWS, Angular)

* Jul 2020 – Dec 2020: Data Science Intern
  * BMW Group, Advanced Analytics team (Powertrain), Munich
  * Cloud data infrastructure (AWS, Spark) processing ~150 TB/day; ML-based root-cause analysis of a battery safety issue

* Oct 2018 – Dec 2019: Data Scientist (part-time)
  * Crossyn Automotive, Tilburg
  * Streaming services for real-time processing of automotive sensor data (Kafka, Docker, PostgreSQL, ClickHouse)

Grants
======
* SURF Compute Call 2025 — Small Compute Grant on Snellius (Dutch national supercomputer), grant no. EINF-13076

Skills
======
* Deep learning: PyTorch, TensorFlow, diffusion models, flow-matching, physics-informed neural networks, distributed/multi-GPU training
* HPC & infrastructure: SLURM (MareNostrum 5, LUMI, Snellius), Kubernetes, Spark, Kafka, AWS, Docker, MLflow, Weights & Biases
* Programming: Python, SQL, Java, Scala, C++, R

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>

Academic service
======
* Reviewer: VLDB 2026 (workshops), VLDB Journal, SIGMOD 2026, MulTiSA 2025 (ICDE workshop), Data Mining and Knowledge Discovery, Journal for Big Data Research
* Publication chair, MulTiSA Workshop on Multivariate Time Series Analysis, ICDE 2024 & 2025
* Co-lecturer, "Big Data Management" (TU/e); supervisor to 8 Master's students
