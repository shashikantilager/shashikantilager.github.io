---
layout: page
permalink: /projects/
title: Projects
description:
nav: true
nav_order: 2
---

{% assign all_projects = site.projects | sort: "importance" | reverse %}
{% assign active = all_projects | where: "status", "ongoing" %}
{% assign past   = all_projects | where: "status", "completed" %}

<div class="proj-list">

  <div class="proj-group">
    <h3 class="proj-group-title">Active Projects <span class="proj-group-count">{{ active.size }}</span></h3>
    {% for p in active %}
      <a href="{{ p.url | relative_url }}" class="proj-row">
        <div class="proj-row-header">
          <span class="proj-title">{{ p.title }}</span>
          <span class="proj-year">{{ p.year }}</span>
        </div>
        {% if p.subtitle %}
          <div class="proj-subtitle">{{ p.subtitle }}</div>
        {% endif %}
        <div class="proj-funding-line">
          <span class="proj-line-label">Funding</span>
          {% if p.funder_logo %}
            <img src="{{ '/assets/img/funders/' | append: p.funder_logo | relative_url }}" alt="{{ p.funder }}" class="proj-funder-logo">
          {% endif %}
          <span class="proj-funder-name">{{ p.funder }}</span>
        </div>
        {% if p.role %}
          <div class="proj-role-line">
            <span class="proj-line-label">Role</span>
            <span class="proj-role-value{% if p.role contains 'PI' or p.role contains 'Coordinator' %} proj-role-pi{% endif %}">{{ p.role }}</span>
          </div>
        {% endif %}
        {% if p.description %}
          <div class="proj-desc">{{ p.description }}</div>
        {% endif %}
        {% if p.tags %}
          <div class="proj-tags">
            {% for tag in p.tags %}
              <span class="proj-tag">{{ tag }}</span>
            {% endfor %}
          </div>
        {% endif %}
      </a>
    {% endfor %}
  </div>

  <div class="proj-group">
    <h3 class="proj-group-title">Completed &amp; Past Grants <span class="proj-group-count">{{ past.size }}</span></h3>
    {% for p in past %}
      <a href="{{ p.url | relative_url }}" class="proj-row proj-row-past">
        <div class="proj-row-header">
          <span class="proj-title">{{ p.title }}</span>
          <span class="proj-year">{{ p.year }}</span>
        </div>
        <div class="proj-funding-line">
          <span class="proj-line-label">Funding</span>
          {% if p.funder_logo %}
            <img src="{{ '/assets/img/funders/' | append: p.funder_logo | relative_url }}" alt="{{ p.funder }}" class="proj-funder-logo">
          {% endif %}
          <span class="proj-funder-name">{{ p.funder }}</span>
          {% if p.amount %}<span class="proj-amount">({{ p.amount }})</span>{% endif %}
        </div>
        {% if p.role %}
          <div class="proj-role-line">
            <span class="proj-line-label">Role</span>
            <span class="proj-role-value">{{ p.role }}</span>
          </div>
        {% endif %}
        {% if p.description %}
          <div class="proj-desc">{{ p.description }}</div>
        {% endif %}
        {% if p.tags %}
          <div class="proj-tags">
            {% for tag in p.tags %}
              <span class="proj-tag">{{ tag }}</span>
            {% endfor %}
          </div>
        {% endif %}
      </a>
    {% endfor %}
  </div>

</div>
