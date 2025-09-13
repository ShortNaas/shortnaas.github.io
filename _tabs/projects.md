---
layout: page
icon: fas fa-project-diagram
order: 2
---

<ul>
  {% for project in site.projects %}
    {% unless project.exclude_from_list %}
      <li>
        <a href="{{ project.url }}" style="font-size: 1.2em; font-weight: bold;">
          {{ project.title }}
        </a>
        <div style="font-size: 1.1em; margin-left: 25px; margin-top: 4px;">
          {{ project.summary }}
        </div>
      </li>
    {% endunless %}
  {% endfor %}
</ul>



