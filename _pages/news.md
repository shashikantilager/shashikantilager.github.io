---
layout: page
permalink: /news/
title: News
description:
nav: true
nav_order: 6
---

{% if site.news != blank %}
  {% assign news_items = site.news | reverse %}
  {% assign current_year = "" %}

  <div class="news-timeline">
    {% for item in news_items %}
      {% assign item_year = item.date | date: '%Y' %}
      {% if item_year != current_year %}
        {% unless forloop.first %}</ul></div>{% endunless %}
        <div class="news-year-group">
          <h3 class="news-year-label">{{ item_year }}</h3>
          <ul class="news-year-list">
        {% assign current_year = item_year %}
      {% endif %}

        <li class="news-timeline-item">
          <span class="news-tl-date">{{ item.date | date: '%b %d' }}</span>
          <span class="news-tl-content">
            {% if item.inline %}
              {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
            {% else %}
              <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
            {% endif %}
          </span>
        </li>

      {% if forloop.last %}</ul></div>{% endif %}
    {% endfor %}
  </div>
{% else %}
  <p>No news yet.</p>
{% endif %}
