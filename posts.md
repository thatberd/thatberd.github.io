---
layout: page
title: Posts
permalink: /posts/
---

## All posts

{% for post in site.posts %}
- **{{ post.date | date: "%b %d, %Y" }}** — [{{ post.title }}]({{ post.url }})
{% endfor %}