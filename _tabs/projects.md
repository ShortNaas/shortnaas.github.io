---
layout: page
icon: fas fa-project-diagram
order: 3
---

<ul>
  {% for project in site.projects %}
    <li><a href="{{ project.url }}">{{ project.title }}</a></li>
  {% endfor %}
</ul>

