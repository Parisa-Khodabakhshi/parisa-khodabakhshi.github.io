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
