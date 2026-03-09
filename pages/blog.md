---
layout: default
title: Blog
description: Articles and updates about Virginia divorce law
permalink: /blog/
---

{% if site.posts.size > 0 %}
<div class="blog-controls">
  <span class="sort-label">Sort by date:</span>
  <button class="sort-btn active" id="sort-newest" onclick="sortPosts('newest')">Newest First</button>
  <button class="sort-btn" id="sort-oldest" onclick="sortPosts('oldest')">Oldest First</button>
</div>

<ul class="post-list" id="post-list">
  {% for post in site.posts %}
  <li data-date="{{ post.date | date: '%s' }}">
    <span class="post-date">{{ post.date | date: "%B %-d, %Y" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% if post.excerpt %}
    <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% else %}
<p>No posts yet. Check back soon.</p>
{% endif %}

<style>
  .blog-controls {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
  }
  .sort-label {
    font-size: 0.85rem;
    color: #666;
  }
  .sort-btn {
    padding: 0.3rem 0.75rem;
    font-size: 0.8rem;
    border: 1px solid #ccc;
    border-radius: 3px;
    background: #f5f5f5;
    color: #444;
    cursor: pointer;
    transition: background 0.15s, color 0.15s, border-color 0.15s;
  }
  .sort-btn:hover {
    background: #e8e8e8;
    border-color: #aaa;
  }
  .sort-btn.active {
    background: #333;
    color: #fff;
    border-color: #333;
  }
  .post-list {
    list-style: none;
    padding: 0;
  }
  .post-list li {
    margin-bottom: 2rem;
    border-bottom: 1px solid #eee;
    padding-bottom: 1.5rem;
  }
  .post-list li:last-child {
    border-bottom: none;
  }
  .post-date {
    display: block;
    color: #666;
    font-size: 0.85rem;
    margin-bottom: 0.25rem;
  }
  .post-list a {
    font-size: 1.1rem;
    font-weight: 600;
  }
  .post-list p {
    margin-top: 0.5rem;
    color: #444;
  }
</style>

<script>
  function sortPosts(order) {
    var list = document.getElementById('post-list');
    var items = Array.from(list.querySelectorAll('li'));

    items.sort(function(a, b) {
      var dateA = parseInt(a.getAttribute('data-date'), 10);
      var dateB = parseInt(b.getAttribute('data-date'), 10);
      return order === 'newest' ? dateB - dateA : dateA - dateB;
    });

    items.forEach(function(item) { list.appendChild(item); });

    document.getElementById('sort-newest').classList.toggle('active', order === 'newest');
    document.getElementById('sort-oldest').classList.toggle('active', order === 'oldest');
  }
</script>
