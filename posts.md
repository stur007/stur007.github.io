---
layout: default
title: All Posts
---

<div class="archive-intro">
  <p>
    This archive gathers notes from particle physics, mathematics, projects, literature, films,
    and occasional miscellany. Use the search box or filters to move through it more deliberately.
  </p>
</div>

<section class="archive-controls">
  <div class="search-box">
    <i class="fas fa-search search-icon"></i>
    <input type="text" id="search-input" class="search-input" placeholder="Search by title..." />
  </div>

  <div class="archive-filters">
    <div class="filter-panel filter-section">
      <h3 class="filter-title">Categories</h3>
      <ul class="filter-list" id="category-filters">
        <li class="filter-item active" data-filter="all">
          <a href="#" onclick="filterPosts('all'); return false;">All</a>
        </li>
        {% for category in site.categories %}
        <li class="filter-item" data-filter="category-{{ category[0] | slugify }}">
          <a href="#" onclick="filterPosts('category-{{ category[0] | slugify }}'); return false;">{{ category[0] }}</a>
        </li>
        {% endfor %}
      </ul>
    </div>

    <div class="filter-panel filter-section">
      <h3 class="filter-title">Tags</h3>
      <ul class="filter-list" id="tag-filters">
        <li class="filter-item active" data-filter="all">
          <a href="#" onclick="filterPosts('all'); return false;">All</a>
        </li>
        {% assign all_tags = "" | split: "" %}
        {% for post in site.posts %}
          {% for tag in post.tags %}
            {% unless all_tags contains tag %}
              {% assign all_tags = all_tags | push: tag %}
            {% endunless %}
          {% endfor %}
        {% endfor %}
        {% assign sorted_tags = all_tags | sort %}
        {% for tag in sorted_tags %}
        <li class="filter-item" data-filter="tag-{{ tag | slugify }}">
          <a href="#" onclick="filterPosts('tag-{{ tag | slugify }}'); return false;">{{ tag }}</a>
        </li>
        {% endfor %}
      </ul>
    </div>
  </div>
</section>

<ul class="post-list archive-list" id="posts-container">
  {% for post in site.posts %}
  <li
    class="post-list-item"
    data-categories="{% for category in post.categories %}category-{{ category | slugify }} {% endfor %}"
    data-tags="{% for tag in post.tags %}tag-{{ tag | slugify }} {% endfor %}"
    data-title="{{ post.title | downcase }}"
  >
    <div class="post-card-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
      {% if post.categories.size > 0 %}
      <span class="category-chip">{{ post.categories[0] }}</span>
      {% endif %}
    </div>

    <h2 class="post-list-title">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>

    {% if post.tags.size > 0 %}
    <div class="tags">
      {% for tag in post.tags limit:4 %}
      <span class="tag">#{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}

    <div class="post-list-excerpt">
      {{ post.excerpt | strip_html | truncatewords: 50 }}
    </div>
    <a href="{{ post.url | relative_url }}" class="read-more">
      Read more
      <i class="fas fa-arrow-right"></i>
    </a>
  </li>
  {% endfor %}
</ul>

<div id="no-results" class="no-results" style="display: none;">
  <p>No posts found matching your criteria.</p>
  <p><a href="#" onclick="filterPosts('all'); return false;">Show all posts</a></p>
</div>

<div class="pagination">
  <a href="{{ site.baseurl }}/">&larr; Back to Home</a>
</div>

<script>
  let currentFilter = 'all';

  document.addEventListener("DOMContentLoaded", function () {
    const searchInput = document.getElementById('search-input');

    searchInput.addEventListener('input', function () {
      filterPosts(currentFilter, this.value.toLowerCase());
    });

    filterPosts('all');
  });

  function setActiveFilters(filterType) {
    const categoryFilters = document.querySelectorAll('#category-filters .filter-item');
    const tagFilters = document.querySelectorAll('#tag-filters .filter-item');
    const categoryAll = document.querySelector('#category-filters [data-filter="all"]');
    const tagAll = document.querySelector('#tag-filters [data-filter="all"]');

    categoryFilters.forEach(item => item.classList.remove('active'));
    tagFilters.forEach(item => item.classList.remove('active'));

    if (filterType === 'all') {
      if (categoryAll) categoryAll.classList.add('active');
      if (tagAll) tagAll.classList.add('active');
      return;
    }

    if (filterType.startsWith('category-')) {
      if (tagAll) tagAll.classList.add('active');
      const selectedCategory = document.querySelector(`#category-filters [data-filter="${filterType}"]`);
      if (selectedCategory) selectedCategory.classList.add('active');
      return;
    }

    if (filterType.startsWith('tag-')) {
      if (categoryAll) categoryAll.classList.add('active');
      const selectedTag = document.querySelector(`#tag-filters [data-filter="${filterType}"]`);
      if (selectedTag) selectedTag.classList.add('active');
    }
  }

  function filterPosts(filterType, searchTerm) {
    const posts = document.querySelectorAll('.post-list-item');
    const noResults = document.getElementById('no-results');
    const searchInput = document.getElementById('search-input');
    let visiblePosts = 0;

    currentFilter = filterType;

    if (typeof searchTerm !== 'string') {
      searchTerm = searchInput ? searchInput.value.toLowerCase() : '';
    }

    setActiveFilters(filterType);

    posts.forEach(post => {
      const categories = post.getAttribute('data-categories');
      const tags = post.getAttribute('data-tags');
      const title = post.getAttribute('data-title');
      let showPost = true;

      if (filterType !== 'all') {
        if (filterType.startsWith('category-') && !categories.includes(filterType)) {
          showPost = false;
        } else if (filterType.startsWith('tag-') && !tags.includes(filterType)) {
          showPost = false;
        }
      }

      if (showPost && searchTerm && !title.includes(searchTerm)) {
        showPost = false;
      }

      if (showPost) {
        post.style.display = 'block';
        visiblePosts++;
      } else {
        post.style.display = 'none';
      }
    });

    if (visiblePosts === 0) {
      noResults.style.display = 'block';
    } else {
      noResults.style.display = 'none';
    }
  }
</script>
