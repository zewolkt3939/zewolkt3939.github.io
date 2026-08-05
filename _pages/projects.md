---
layout: page
title: projects
permalink: /projects/
description: Selected cybersecurity projects, internships, and labs — prioritized for depth and evidence over volume.
nav: true
nav_order: 1
display_categories: [cybersecurity, infrastructure]
horizontal: false
---

I keep this page short on purpose. Each item is something I can walk through in an interview: problem, my role, stack, and what was verified.

**Start here:** [AI-APW (capstone SIEM triage)]({{ '/projects/10_ai_apw/' | relative_url }}) · [Malware analysis platform]({{ '/projects/02_malware_analysis/' | relative_url }}) · [CV / PDF]({{ '/cv/' | relative_url }})

<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
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

{% assign sorted_projects = site.projects | sort: "importance" %}

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
