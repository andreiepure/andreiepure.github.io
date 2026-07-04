---
layout: page
title: Books
permalink: /books/
description: "Books I've been reading."
---

<style>
  .book-title {
    font-weight: 600;
  }
  .book-author {
    font-style: italic;
    color: #666;
  }
  .book-status.finished {
    color: #22c55e;
    font-size: 1.2em;
  }
</style>

<h1>Books</h1>

<div class="page-intro">Tracking books that:
	<ul>
		<li>✅ I read and want to remember.</li>
		<li>📖 I've started, and I'd like to get back and finish at some point.</li>
	</ul>
<p> I am trilingual (Romanian, English and French) and this is reflected in my lectures.</p>
</div>

{% assign books_by_year = site.data.books | group_by: "year" | sort: "name" | reverse %}
{% for year_group in books_by_year %}
<h2>{{ year_group.name }}</h2>
<ul class="books-list">
  {% for book in year_group.items %}
  <li class="{% if book.finished %}finished{% else %}in-progress{% endif %}">
    <span class="book-title">{{ book.title }}</span>
    <span class="book-author">{{ book.author }}</span>
    <span class="book-language">{{ book.language }}</span>
    <span class="book-status {% if book.finished %}finished{% endif %}">{% if book.finished %}✅{% else %}📖{% endif %}</span>
  </li>
  {% endfor %}
</ul>
{% endfor %}
