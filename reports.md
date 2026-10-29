---
layout: default
title: All Reports
permalink: /reports/
---

<section class="page-heading">
  <p class="eyebrow">DATABASE / INDEX</p>
  <h1>All reports</h1>
  <p>Search by report title, ID, location, subject, faction, or tag.</p>
</section>

<label class="search-box" for="report-search">
  <span aria-hidden="true">⌕</span>
  <input id="report-search" type="search" placeholder="Search reports..." autocomplete="off">
  <kbd>/</kbd>
</label>

<p class="result-count" id="result-count" aria-live="polite"></p>

<div class="report-grid" id="report-list">
  {% assign reports = site.reports | sort: "date" | reverse %}
  {% for report in reports %}
    {% include report-card.html report=report %}
  {% endfor %}
</div>
<p class="empty-state" id="no-results" hidden>No reports match your search.</p>

<script>
(() => {
  const input = document.getElementById('report-search');
  const cards = [...document.querySelectorAll('[data-report-card]')];
  const count = document.getElementById('result-count');
  const empty = document.getElementById('no-results');

  function filterReports() {
    const query = input.value.trim().toLowerCase();
    let visible = 0;
    cards.forEach(card => {
      const matches = card.dataset.search.includes(query);
      card.hidden = !matches;
      if (matches) visible++;
    });
    count.textContent = `${visible} ${visible === 1 ? 'report' : 'reports'}`;
    empty.hidden = visible !== 0;
  }

  input.addEventListener('input', filterReports);
  document.addEventListener('keydown', event => {
    if (event.key === '/' && !['INPUT', 'TEXTAREA'].includes(document.activeElement.tagName)) {
      event.preventDefault();
      input.focus();
    }
    if (event.key === 'Escape' && document.activeElement === input) {
      input.value = '';
      filterReports();
      input.blur();
    }
  });
  filterReports();
})();
</script>
