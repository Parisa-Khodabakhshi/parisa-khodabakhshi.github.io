---
layout: page
permalink: /publications/
title: Publications
description: Publications in reversed chronological order.
nav: true
nav_order: 2
---

{% include bib_search.liquid %}

<style>
  /* Preserve the al-folio year labels on the right */
  .bibliography .year {
    float: right;
    margin-left: 1rem;
    color: var(--global-text-color);
    font-weight: 600;
  }

  /* Use one continuous publication counter across both sections */
  .numbered-publications {
    counter-reset: publication-counter 14;
  }

  .numbered-publications ol.bibliography {
    list-style: none;
    padding-left: 0;
  }

  .numbered-publications ol.bibliography > li {
    position: relative;
    counter-increment: none;
    counter-decrement: publication-counter;
    padding-left: 2.25rem;
  }

  .numbered-publications ol.bibliography > li::before {
    content: counter(publication-counter) ".";
    position: absolute;
    left: 0;
    top: 0;
    font-weight: 600;
    color: var(--global-text-color);
  }

  /* Add substantial spacing before conference papers */
  .conference-publications {
    margin-top: 4.5rem;
    padding-top: 1rem;
    border-top: 1px solid var(--global-divider-color);
  }

  .conference-publications h2 {
    margin-bottom: 2rem;
  }
</style>

<div class="numbered-publications">

  <section class="journal-publications">

    ## Journal Papers

    {% bibliography --query @article --prefix journal %}

  </section>

  <section class="conference-publications">

    ## Conference Papers

    {% bibliography --query @inproceedings --prefix conference %}

  </section>

</div>
