---
layout: page
title: Book Notes
summary: >
    A detailed book notes from books I've read.
---

<div style="margin-bottom: 20px; font-size: 0.9em;">
  Sort by: 
  <span onclick="sortBooks('title')" style="color: #18ad30; cursor: pointer; margin-right: 12px; text-decoration: none; transition: color 0.2s ease; display: inline-block;" onmouseover="this.style.color='#173b23';" onmouseout="this.style.color='#18ad30';">title</span>
  <span onclick="sortBooks('rating')" style="color: #18ad30; cursor: pointer; margin-right: 12px; text-decoration: none; transition: color 0.2s ease; display: inline-block;" onmouseover="this.style.color='#173b23';" onmouseout="this.style.color='#18ad30';">best</span>
  <span onclick="sortBooks('date')" style="color: #18ad30; cursor: pointer; text-decoration: none; transition: color 0.2s ease; display: inline-block;" onmouseover="this.style.color='#173b23';" onmouseout="this.style.color='#18ad30';">date</span>
</div>

<ul id="booksList">
{% assign sorted_books = site.projects 
  | where: "category", "books" 
  | where_exp: "book", "book.title != 'Books'" 
  | sort: "date_read" 
  | reverse 
  | sort: "rating" 
  | reverse 
  | sort: "title" %}

{% for book in sorted_books %}
  <li style="display: flex; align-items: flex-start; margin-bottom: 30px;" 
      data-title="{{ book.title }}" 
      data-rating="{{ book.rating }}" 
      data-date="{{ book.date_read }}">
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
{% endfor %}
</ul>

<script>
let currentSort = 'title';
let isReversed = false;

function sortBooks(sortBy) {
  const booksList = document.getElementById('booksList');
  const books = Array.from(booksList.querySelectorAll('li'));
  
  // Toggle reverse if same button clicked
  if (sortBy === currentSort) {
    isReversed = !isReversed;
  } else {
    isReversed = false;
    currentSort = sortBy;
  }
  
  books.sort((a, b) => {
    let comparison = 0;
    
    if (sortBy === 'title') {
      comparison = a.dataset.title.localeCompare(b.dataset.title);
    } else if (sortBy === 'rating') {
      const ratingDiff = parseFloat(b.dataset.rating) - parseFloat(a.dataset.rating);
      if (ratingDiff !== 0) {
        comparison = ratingDiff;
      } else {
        comparison = a.dataset.title.localeCompare(b.dataset.title);
      }
    } else if (sortBy === 'date') {
      comparison = new Date(b.dataset.date) - new Date(a.dataset.date);
    }
    
    return isReversed ? -comparison : comparison;
  });
  
  books.forEach(book => booksList.appendChild(book));
}
</script>


