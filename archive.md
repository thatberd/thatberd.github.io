---
layout: default
title: Posts
permalink: /posts/
---

# posts

---

Browse all blog posts.

<div class="post-grid">
  {% for post in site.posts %}
    <a href="{{ post.url | relative_url }}" class="post-card">
      <div class="post-card-content">
        <h2>{{ post.title }}</h2>
        <p class="post-date">{{ post.date | date: "%b %d, %Y" }}</p>
        <p class="post-excerpt">
          {{ post.excerpt | strip_html | truncate: 120 }}
        </p>
      </div>
    </a>
  {% endfor %}
</div>
