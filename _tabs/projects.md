---
layout: page
icon: fas fa-project-diagram
order: 3
---

<ul>
  {% for project in site.projects %}
    {% unless project.exclude_from_list %}
      <li><a href="{{ project.url }}">{{ project.title }}</a></li>
    {% endunless %}
  {% endfor %}
</ul>


