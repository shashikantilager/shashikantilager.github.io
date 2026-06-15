---
layout: page
permalink: /pagestats/
title: Visitor Statistics
nav: false
sitemap: false
robots: noindex, nofollow
---

<style>
.stats-link-box {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border: 1px solid var(--global-divider-color);
  border-radius: 8px;
  padding: 1.5rem 2rem;
  margin: 1.5rem 0;
}
.stats-link-box .stats-desc {
  font-size: 0.9rem;
  color: var(--global-text-color-light);
}
.stats-link-box a.stats-btn {
  display: inline-block;
  padding: 0.5rem 1.2rem;
  background: var(--global-theme-color);
  color: #fff !important;
  border-radius: 4px;
  font-size: 0.88rem;
  font-weight: 600;
  text-decoration: none;
  white-space: nowrap;
  margin-left: 1.5rem;
  flex-shrink: 0;
}
.stats-counter-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1rem;
  margin-top: 1.5rem;
}
.stats-counter-box {
  border: 1px solid var(--global-divider-color);
  border-radius: 8px;
  padding: 1.2rem;
  text-align: center;
}
.stats-counter-box .stat-num {
  font-size: 2rem;
  font-weight: 700;
  color: var(--global-theme-color);
  line-height: 1;
}
.stats-counter-box .stat-label {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--global-text-color-light);
  margin-top: 0.4rem;
}
</style>

<p style="font-size:0.82rem; color:var(--global-text-color-light);">
  <em>This page is not indexed or linked from the site. Access it directly at <code>/pagestats</code>.</em>
</p>

<div class="stats-link-box">
  <div class="stats-desc">
    Full visitor analytics — page views, countries, referrers, and browser stats —
    powered by <strong>GoatCounter</strong>.
  </div>
  <a class="stats-btn" href="https://shashikantilager.goatcounter.com/" target="_blank" rel="noopener">
    Open Stats Dashboard &rarr;
  </a>
</div>

<div class="stats-counter-grid">
  <div class="stats-counter-box">
    <div class="stat-num"><span class="goatcounter-count" data-path="/"></span></div>
    <div class="stat-label">Home</div>
  </div>
  <div class="stats-counter-box">
    <div class="stat-num"><span class="goatcounter-count" data-path="/publications/"></span></div>
    <div class="stat-label">Publications</div>
  </div>
  <div class="stats-counter-box">
    <div class="stat-num"><span class="goatcounter-count" data-path="/projects/"></span></div>
    <div class="stat-label">Projects</div>
  </div>
  <div class="stats-counter-box">
    <div class="stat-num"><span class="goatcounter-count" data-path="/supervision/"></span></div>
    <div class="stat-label">Team</div>
  </div>
</div>
