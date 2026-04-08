---
layout: page
title: Home
---

<div class="intro">
  <h2>Hi!</h2>

  <p>This is my learning blog.</p>
  <p>I update this blog with interesting things I learn, related or unrelated to programming.</p>
</div>

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