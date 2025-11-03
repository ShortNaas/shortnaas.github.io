---
layout: page
title: Book Notes
summary: >
    A detailed book notes from books I've read.
---

<ul>
{% for book in site.projects %}
  {% if book.category == "books" and book.title != "Books" %}
    <li style="display: flex; align-items: flex-start; margin-bottom: 30px;">
      <a href="{{ book.url | relative_url }}">
        <img src="{{ book.image | relative_url }} " alt="{{ book.title }} book cover" 
             style="height:120px; width:92px; object-fit:cover; margin-right: 60px; box-shadow: 0 4px 16px rgba(0,0,0,0.2);">
      </a>
      <div>
        <a href="{{ book.url | relative_url }}" 
           style="font-size: 1.3em; font-weight: bold;">
          {{ book.title }}
        </a>
        <div style="font-size: 0.95em; color: #666;">
            Date Read: {{ book.date_read }}. How Strongly I Recommend It: {{ book.rating }}/10
        </div>
        <div style="margin-top: 10px;">
        {{ book.summary }}
        </div>
      </div>
    </li>
  {% endif %}
{% endfor %}
</ul>



