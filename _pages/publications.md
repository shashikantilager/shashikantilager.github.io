---
layout: page
permalink: /publications/
title: Publications
description:
nav: true
nav_order: 1
---

Full list on [Google Scholar](https://scholar.google.com.au/citations?user=qBnfuW4AAAAJ&hl=en).

<div class="pub-filter-bar">
  <div class="pub-filter-group">
    <span class="pub-filter-label">Type</span>
    <button class="pub-filter-btn active" data-filter-type="all">All</button>
    <button class="pub-filter-btn" data-filter-type="journal">Journal</button>
    <button class="pub-filter-btn" data-filter-type="conference">Conference</button>
    <button class="pub-filter-btn" data-filter-type="workshop">Workshop</button>
  </div>
  <div class="pub-filter-group">
    <span class="pub-filter-label">Year</span>
    <select id="pub-year-select" class="pub-year-select">
      <option value="all">All years</option>
    </select>
  </div>
  <div class="pub-filter-group pub-filter-count">
    <span id="pub-count"></span>
  </div>
</div>

<div class="publications" id="pub-list">
{% bibliography --query @*[hidden != true] --group_by year --group_order descending -f {{ site.scholar.bibliography }} %}
</div>

### Book Chapters

<div class="publications">
{% bibliography --query @incollection --group_by none -f {{ site.scholar.bibliography }} %}
</div>

<script>
(function () {
  // Populate year dropdown from rendered entries
  const yearSelect = document.getElementById('pub-year-select');
  const years = new Set();
  document.querySelectorAll('.pub-row[data-year]').forEach(function (r) {
    if (r.dataset.year) years.add(r.dataset.year);
  });
  Array.from(years).sort(function (a, b) { return b - a; }).forEach(function (y) {
    const opt = document.createElement('option');
    opt.value = y;
    opt.textContent = y;
    yearSelect.appendChild(opt);
  });

  let activeType = 'all';
  let activeYear = 'all';

  function applyFilters() {
    let visible = 0;
    document.querySelectorAll('.pub-row').forEach(function (row) {
      const typeMatch = activeType === 'all' || row.dataset.type === activeType;
      const yearMatch = activeYear === 'all' || row.dataset.year === activeYear;
      const show = typeMatch && yearMatch;
      row.closest('li').style.display = show ? '' : 'none';
      if (show) visible++;
    });

    document.querySelectorAll('#pub-list h2').forEach(function (h2) {
      let sibling = h2.nextElementSibling;
      let hasVisible = false;
      while (sibling && sibling.tagName !== 'H2') {
        if (sibling.tagName === 'OL') {
          if (sibling.querySelectorAll('li:not([style*="none"])').length > 0) hasVisible = true;
        }
        sibling = sibling.nextElementSibling;
      }
      h2.style.display = hasVisible ? '' : 'none';
    });

    const countEl = document.getElementById('pub-count');
    if (countEl) countEl.textContent = visible + ' paper' + (visible !== 1 ? 's' : '');
  }

  document.addEventListener('click', function (e) {
    const btn = e.target.closest('.pub-filter-btn');
    if (!btn || !('filterType' in btn.dataset)) return;
    activeType = btn.dataset.filterType;
    btn.closest('.pub-filter-group').querySelectorAll('.pub-filter-btn').forEach(function (b) {
      b.classList.toggle('active', b === btn);
    });
    applyFilters();
  });

  yearSelect.addEventListener('change', function () {
    activeYear = yearSelect.value;
    applyFilters();
  });

  applyFilters();
})();
</script>
