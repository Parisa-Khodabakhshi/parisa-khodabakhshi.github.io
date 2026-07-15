---
layout: page
title: news
permalink: /news/
nav: true
nav_order: 5
---

<div id="news-list">
  {% assign sorted_news = site.news | sort: "date" | reverse %}

  {% for item in sorted_news %}
    <div class="news-entry">
      <div class="news-date">
        {{ item.date | date: "%B %-d, %Y" }}
      </div>

      <div class="news-content">
        {{ item.content }}
      </div>
    </div>
  {% endfor %}
</div>

<nav id="news-pagination" aria-label="News pagination">
  <button id="news-prev" type="button">Previous</button>

  <span id="news-page-numbers"></span>

  <button id="news-next" type="button">Next</button>
</nav>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const entries = Array.from(document.querySelectorAll(".news-entry"));
    const itemsPerPage = 20;
    const totalPages = Math.ceil(entries.length / itemsPerPage);

    const previousButton = document.getElementById("news-prev");
    const nextButton = document.getElementById("news-next");
    const pageNumbers = document.getElementById("news-page-numbers");

    let currentPage = 1;

    function displayPage(page) {
      currentPage = page;

      const start = (page - 1) * itemsPerPage;
      const end = start + itemsPerPage;

      entries.forEach(function (entry, index) {
        entry.style.display =
          index >= start && index < end ? "block" : "none";
      });

      previousButton.disabled = currentPage === 1;
      nextButton.disabled = currentPage === totalPages;

      renderPageNumbers();

      window.scrollTo({
        top: 0,
        behavior: "smooth"
      });
    }

    function renderPageNumbers() {
      pageNumbers.innerHTML = "";

      for (let page = 1; page <= totalPages; page++) {
        const button = document.createElement("button");
        button.type = "button";
        button.textContent = page;

        if (page === currentPage) {
          button.classList.add("active");
          button.setAttribute("aria-current", "page");
        }

        button.addEventListener("click", function () {
          displayPage(page);
        });

        pageNumbers.appendChild(button);
      }
    }

    previousButton.addEventListener("click", function () {
      if (currentPage > 1) {
        displayPage(currentPage - 1);
      }
    });

    nextButton.addEventListener("click", function () {
      if (currentPage < totalPages) {
        displayPage(currentPage + 1);
      }
    });

    if (entries.length === 0) {
      document.getElementById("news-pagination").style.display = "none";
    } else {
      displayPage(1);
    }
  });
</script>

<style>
  .news-entry {
    margin-bottom: 1.5rem;
    padding-bottom: 1.25rem;
    border-bottom: 1px solid var(--global-divider-color);
  }

  .news-date {
    margin-bottom: 0.35rem;
    font-weight: 600;
    color: var(--global-theme-color);
  }

  .news-content p:last-child {
    margin-bottom: 0;
  }

  #news-pagination {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    gap: 0.4rem;
    margin-top: 2rem;
  }

  #news-pagination button {
    padding: 0.4rem 0.7rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 0.25rem;
    color: var(--global-text-color);
    background: var(--global-bg-color);
    cursor: pointer;
  }

  #news-pagination button:hover,
  #news-pagination button.active {
    color: var(--global-bg-color);
    background: var(--global-theme-color);
  }

  #news-pagination button:disabled {
    cursor: not-allowed;
    opacity: 0.45;
  }
</style>
