---
layout: default
title: Home
permalink: /
---

<section class="hero">
  <p class="eyebrow">FIELD REPORTS DATABASE</p>
  <p class="hero-copy">A searchable archive of field reports, encounters, and faction intelligence by Tybo</p>
  <a class="button" href="{{ '/reports/' | relative_url }}">Browse reports <span aria-hidden="true">→</span></a>
</section>

<section class="section-heading">
  <div>
    <p class="eyebrow">DATABASE</p>
    <h2>Latest reports</h2>
  </div>
  <a class="text-link" href="{{ '/reports/' | relative_url }}">View all reports →</a>
</section>

<div class="report-grid">
  {% assign reports = site.reports | sort: "date" | reverse %}
  {% for report in reports limit: 6 %}
    {% include report-card.html report=report %}
  {% endfor %}
  {% if reports.size == 0 %}
    <p class="empty-state">No reports yet. Add a Markdown file to <code>_reports/</code>.</p>
  {% endif %}
</div>
