---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
excerpt: "Curriculum vitae of Jens d'Hondt: PhD in computer science from TU Eindhoven, postdoc at the Barcelona Supercomputing Center, publications, talks and service."
redirect_from:
  - /resume
---

{% include base_path %}

<div class="cv">

<div class="cv-intro">
  <p>Postdoctoral Scientist at the Barcelona Supercomputing Center, working on generative AI for atmospheric chemistry. PhD in Computer Science from TU Eindhoven on multivariate similarity search.</p>
  <div class="cv-actions">
    <a class="btn btn--primary" href="{{ base_path }}/files/postdoc25.pdf"><i class="fas fa-file-pdf" aria-hidden="true"></i> Download PDF</a>
    <a class="btn btn--inverse" href="{{ base_path }}/publications/"><i class="fas fa-book" aria-hidden="true"></i> Publications</a>
    <a class="btn btn--inverse" href="{{ base_path }}/talks/"><i class="fas fa-microphone" aria-hidden="true"></i> Talks</a>
  </div>
</div>

<h2 id="experience">Experience</h2>

<ol class="cv-timeline">
  <li class="cv-entry cv-entry--current">
    <div class="cv-entry__when">Dec 2025 – present</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Postdoctoral Scientist</h3>
      <p class="cv-entry__org">Barcelona Supercomputing Center (BSC), Earth Sciences Department</p>
      <p>Generative AI methods for downscaling atmospheric chemistry simulations: diffusion models, flow-matching, and physics-constrained CNNs with hard constraints such as mass conservation.</p>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">Nov 2021 – Dec 2025</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Doctoral Researcher</h3>
      <p class="cv-entry__org">Eindhoven University of Technology, Data &amp; AI cluster</p>
      <ul>
        <li>Scalable multivariate time-series similarity search algorithms, published at VLDB, VLDB Journal, SIGMOD and ICDE</li>
        <li>Led work in the EU-funded STELAR project on ML pipelines for agricultural field delineation from satellite imagery</li>
      </ul>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">Dec 2019 – Nov 2021</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Freelance Software Engineer</h3>
      <p>Data-driven applications and statistical analyses for clients (Python, Spark, Kafka, TensorFlow, AWS, Angular).</p>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">Jul 2020 – Dec 2020</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Data Science Intern</h3>
      <p class="cv-entry__org">BMW Group, Advanced Analytics team (Powertrain), Munich</p>
      <p>Cloud data infrastructure (AWS, Spark) processing ~150 TB/day; ML-based root-cause analysis of a battery safety issue.</p>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">Oct 2018 – Dec 2019</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Data Scientist <span class="cv-tag">part-time</span></h3>
      <p class="cv-entry__org">Crossyn Automotive, Tilburg</p>
      <p>Streaming services for real-time processing of automotive sensor data (Kafka, Docker, PostgreSQL, ClickHouse).</p>
    </div>
  </li>
</ol>

<h2 id="education">Education</h2>

<ol class="cv-timeline">
  <li class="cv-entry">
    <div class="cv-entry__when">Nov 2021 – Dec 2025</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">Ph.D. in Computer Science</h3>
      <p class="cv-entry__org">Eindhoven University of Technology (TU/e)</p>
      <ul>
        <li>Thesis: <a href="{{ base_path }}/publication/phd_thesis_2025"><em>Effective and Efficient Multivariate Similarity Search</em></a></li>
        <li>Supervisors: dr. Odysseas Papapetrou and prof. dr. George Fletcher</li>
      </ul>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">2019 – 2021</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">M.Sc. in Data Science and Artificial Intelligence <span class="cv-tag cv-tag--honor">Cum Laude</span></h3>
      <p class="cv-entry__org">TU/e · GPA 9.1/10</p>
    </div>
  </li>
  <li class="cv-entry">
    <div class="cv-entry__when">2016 – 2019</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">B.Sc. in Industrial Engineering <span class="cv-tag cv-tag--honor">Cum Laude</span></h3>
      <p class="cv-entry__org">TU/e · GPA 8.5/10</p>
    </div>
  </li>
</ol>

<h2 id="skills">Skills</h2>

<div class="cv-skills">
  <div class="cv-skills__group">
    <h3>Deep learning</h3>
    <ul class="cv-chips">
      <li>PyTorch</li><li>TensorFlow</li><li>Diffusion models</li><li>Flow-matching</li><li>Physics-informed neural networks</li><li>Distributed / multi-GPU training</li>
    </ul>
  </div>
  <div class="cv-skills__group">
    <h3>HPC &amp; infrastructure</h3>
    <ul class="cv-chips">
      <li>SLURM (MareNostrum 5, LUMI, Snellius)</li><li>Kubernetes</li><li>Spark</li><li>Kafka</li><li>AWS</li><li>Docker</li><li>MLflow</li><li>Weights &amp; Biases</li>
    </ul>
  </div>
  <div class="cv-skills__group">
    <h3>Programming</h3>
    <ul class="cv-chips">
      <li>Python</li><li>SQL</li><li>Java</li><li>Scala</li><li>C++</li><li>R</li>
    </ul>
  </div>
</div>

<h2 id="publications">Publications</h2>

<ol class="cv-list">
{% for post in site.publications reversed %}
  {% case post.category %}
    {% when 'manuscripts' %}{% assign kind = 'Journal' %}
    {% when 'preprints' %}{% assign kind = 'Preprint' %}
    {% when 'theses' %}{% assign kind = 'Thesis' %}
    {% else %}{% if post.venue contains 'Workshop' %}{% assign kind = 'Workshop' %}{% else %}{% assign kind = 'Conference' %}{% endif %}
  {% endcase %}
  <li class="cv-list__item">
    <span class="cv-list__year">{{ post.date | date: '%Y' }}</span>
    <div class="cv-list__body">
      <a class="cv-list__title" href="{{ base_path }}{{ post.url }}">{{ post.title }}</a>
      <div class="cv-list__meta"><span class="cv-badge cv-badge--{{ kind | downcase }}">{{ kind }}</span> {{ post.venue }}</div>
    </div>
  </li>
{% endfor %}
</ol>

<h2 id="talks">Talks</h2>

<ol class="cv-list">
{% for post in site.talks reversed %}
  <li class="cv-list__item">
    <span class="cv-list__year">{{ post.date | date: '%Y' }}</span>
    <div class="cv-list__body">
      <a class="cv-list__title" href="{{ base_path }}{{ post.url }}">{{ post.title }}</a>
      <div class="cv-list__meta">{{ post.venue }} · {{ post.location }}</div>
    </div>
  </li>
{% endfor %}
</ol>

<h2 id="service">Academic service</h2>

<ul class="cv-service">
  <li><strong>Reviewer:</strong> VLDB 2026 (workshops), VLDB Journal, SIGMOD 2026, MulTiSA 2025 (ICDE workshop), Data Mining and Knowledge Discovery, Journal for Big Data Research</li>
  <li><strong>Publication chair:</strong> MulTiSA Workshop on Multivariate Time Series Analysis, ICDE 2024 &amp; 2025</li>
  <li><strong>Teaching:</strong> co-lecturer, "Big Data Management" (TU/e); supervisor to 8 Master's students</li>
</ul>

<h2 id="grants">Grants</h2>

<ol class="cv-timeline">
  <li class="cv-entry">
    <div class="cv-entry__when">2025</div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">SURF Compute Call, Small Compute Grant</h3>
      <p class="cv-entry__org">Snellius (Dutch national supercomputer) · grant no. EINF-13076</p>
    </div>
  </li>
</ol>

</div>
