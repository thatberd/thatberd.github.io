---
layout: page
title: Home
---

## Hi!

This is my learning blog.

---

## Recent posts

<div class="post-grid">
  {% for post in site.posts limit:3 %}
    <a class="post-card" href="{{ post.url }}">
      <div class="post-card-content">
        <div class="post-date">
          {{ post.date | date: "%b %d, %Y" }}
        </div>
        <div class="post-title">
          {{ post.title }}
        </div>
      </div>
    </a>
  {% endfor %}
</div>
---
