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
* Ph.D. in Computer Science, Eindhoven University of Technology (TU/e), 2025
  * Thesis: *Efficient Algorithms for Multivariate Similarity Search*
  * Supervisor: Odysseas Papapetrou
<!-- TODO: add M.Sc./B.Sc. entries -->

Work experience
======
* Dec 2025 – present: Postdoctoral Scientist
  * Barcelona Supercomputing Center (BSC), Earth Sciences Department
  * ML-based downscaling of atmospheric composition simulations with physics-based constraints

* <!-- TODO: start year --> – 2025: Doctoral Researcher
  * Eindhoven University of Technology, Data & AI cluster
  * Efficient algorithms for multivariate similarity search and correlation analysis; contributor to the EU-funded STELAR project

Skills
======
* Programming: Python (PyTorch), Java, Scala, SQL
* Systems: HPC clusters (SLURM — MareNostrum, Snellius), Spark, AWS, Docker
* Experiment tracking: MLflow, Weights & Biases

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
