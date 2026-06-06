---
layout: default
title: Posts
permalink: /posts/
---

# posts

---

Browse all blog posts.

<!-- Search bar -->
<input type="text" id="post-search" placeholder="Search posts..." />

{% assign posts_by_month = site.posts | group_by_exp:"post", "post.date | date: '%B %Y'" %}

{% for month in posts_by_month %}
  <h2 class="month-heading">{{ month.name }}</h2>
  <div class="post-grid month-group" data-month="{{ month.name }}">
    {% for post in month.items %}
      <a href="{{ post.url | relative_url }}" class="post-card" data-title="{{ post.title | downcase }}" data-excerpt="{{ post.excerpt | strip_html | downcase }}">
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
{% endfor %}

<script>
  document.getElementById('post-search').addEventListener('input', function () {
    const query = this.value.toLowerCase();
    const cards = document.querySelectorAll('.post-card');
    cards.forEach(card => {
      const title = card.getAttribute('data-title') || '';
      const excerpt = card.getAttribute('data-excerpt') || '';
      if (title.includes(query) || excerpt.includes(query)) {
        card.style.display = '';
      } else {
        card.style.display = 'none';
      }
    });
  });
</script>
