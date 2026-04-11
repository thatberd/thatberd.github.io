---
layout: page
title: home
---

---

<div class="intro">
  <h2>Hi!</h2>

  <p>This is my learning blog.</p>
  <p>I update this blog with interesting things I learn, related or unrelated to programming.</p>
</div>

---

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