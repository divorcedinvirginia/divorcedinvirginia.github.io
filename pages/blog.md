---
layout: default
title: Blog
description: Articles and updates about Virginia divorce law
permalink: /blog/
---

{% if site.posts.size > 0 %}
<ul class="post-list">
  {% for post in site.posts %}
  <li>
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
