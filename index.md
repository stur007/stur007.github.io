---
layout: default
title: Home
---

# Hi, there👋

Welcome to my personal website!  
Here you'll find my blog posts, projects, and contact information.

## 📝 Latest Blog Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%Y-%m-%d" }}
    </li>
  {% endfor %}
</ul>

> Powered by [Jekyll](https://jekyllrb.com) and [GitHub Pages](https://pages.github.com)
