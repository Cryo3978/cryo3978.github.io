---
layout: page
title: 项目
permalink: /zh/projects/
description: 持续更新中的项目与实用工具集合。
nav: true
nav_order: 3
locale: zh
translation_key: projects-index
display_categories: [work, fun]
horizontal: false
---

<!-- pages/projects_zh.md -->
<div class="projects">
{% assign current_locale = page.locale | default: site.lang | default: 'en' %}
{% assign locale_strings = site.data.i18n[current_locale] %}
{% assign locale_projects = site.projects | where: "locale", current_locale %}
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  {% assign category_label = locale_strings.project_categories[category] | default: category %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category_label }}</h2>
  </a>
  {% assign categorized_projects = locale_projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = locale_projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
