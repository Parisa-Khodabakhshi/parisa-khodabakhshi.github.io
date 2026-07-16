---
layout: page
permalink: /publications/
title: publications
description: Publications in reverse chronological order.
nav: true
nav_order: 2
---

<style>
  .post-title {
    display: none;
  }

  .post-header {
    margin-bottom: 0;
  }

  .conference-section {
    margin-top: 4rem;
  }
</style>

<p>
If you have any questions regarding my publications or would like to request a copy of a paper, please feel free to <a href="mailto:pak322@lehigh.edu">contact me</a>. A complete and up-to-date list of my publications, citations, and research metrics is also available on <a href="https://scholar.google.com/citations?user=lYr_g-MAAAAJ" target="_blank">Google Scholar</a>.
</p>

<!-- Bibsearch feature -->
{% include bib_search.liquid %}

<div class="publications">

  <h2>Journal Papers</h2>

  {% bibliography --query @article --prefix journal %}

  <div class="conference-section">
    <h2>Conference Proceedings</h2>

    {% bibliography --query @inproceedings --prefix conference %}
  </div>

</div>
