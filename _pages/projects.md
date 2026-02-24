---
layout: page
permalink: /projects/
title: Projects
description:
nav: false
---

{% assign sorted_projects = site.projects | sort: "importance" %}

<ol class="project-enumeration">
  {% for project in sorted_projects limit: 6 %}
    <li>
      <strong>{{ project.title }}</strong><br>
      {% if project.description %}
        <em>{{ project.description }}</em><br>
      {% endif %}
      {% if project.role %}
        Role: {{ project.role }}<br>
      {% endif %}
      {% if project.year %}
        Year: {{ project.year }}<br>
      {% endif %}
      {% unless project.hide_link == true or project.hide_link == "true" %}
        {% if project.link_text %}
          Link: {{ project.link_text }}
        {% elsif project.external_link %}
          Link: <a href="{{ project.external_link }}" target="_blank" rel="noopener noreferrer">Project page</a>
        {% else %}
          Link: <a href="{{ project.url | relative_url }}">Project page</a>
        {% endif %}
      {% endunless %}
    </li>
  {% endfor %}
</ol>
