---
layout: default
title: All Posts
---

<!-- Search Box -->
<div class="search-box">
  <i class="fas fa-search search-icon"></i>
  <input type="text" id="search-input" class="search-input" placeholder="Search posts...">
</div>

<!-- Category Filters -->
<div class="filter-section">
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

<!-- Tag Filters -->
<div class="filter-section">
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

<!-- Posts List -->
<ul class="post-list" id="posts-container">
  {% for post in site.posts %}
    <li class="post-list-item" 
        data-categories="{% for category in post.categories %}category-{{ category | slugify }} {% endfor %}"
        data-tags="{% for tag in post.tags %}tag-{{ tag | slugify }} {% endfor %}"
        data-title="{{ post.title | downcase }}">
      <h2 class="post-list-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      <div class="post-meta">
        Published on {{ post.date | date: "%B %d, %Y" }}
      </div>
      <div class="post-list-excerpt">
        {{ post.excerpt | strip_html | truncatewords: 50 }}
      </div>
      <a href="{{ post.url | relative_url }}" class="read-more">Read more →</a>
    </li>
  {% endfor %}
</ul>

<!-- No results message (hidden by default) -->
<div id="no-results" class="no-results" style="display: none;">
  <p>No posts found matching your criteria.</p>
  <p><a href="#" onclick="filterPosts('all'); return false;">Show all posts</a></p>
</div>

<!-- Back to Home -->
<div class="pagination">
  <a href="{{ site.baseurl }}/">&larr; Back to Home</a>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    // Search functionality
    const searchInput = document.getElementById('search-input');
    searchInput.addEventListener('input', function() {
      filterPosts('all', this.value.toLowerCase());
    });
  });
  
  // Filter posts by category, tag, or search
  function filterPosts(filterType, searchTerm = '') {
    const posts = document.querySelectorAll('.post-list-item');
    const categoryFilters = document.querySelectorAll('#category-filters .filter-item');
    const tagFilters = document.querySelectorAll('#tag-filters .filter-item');
    const noResults = document.getElementById('no-results');
    let visiblePosts = 0;
    
    // Reset all filters
    categoryFilters.forEach(item => item.classList.remove('active'));
    tagFilters.forEach(item => item.classList.remove('active'));
    
    // Activate the selected filter
    if (filterType === 'all') {
      document.querySelector('[data-filter="all"]').classList.add('active');
    } else if (filterType.startsWith('category-')) {
      document.querySelector(`[data-filter="${filterType}"]`).classList.add('active');
    } else if (filterType.startsWith('tag-')) {
      document.querySelector(`[data-filter="${filterType}"]`).classList.add('active');
    }
    
    // Filter posts
    posts.forEach(post => {
      const categories = post.getAttribute('data-categories');
      const tags = post.getAttribute('data-tags');
      const title = post.getAttribute('data-title');
      let showPost = true;
      
      // Apply category/tag filter
      if (filterType !== 'all') {
        if (filterType.startsWith('category-') && !categories.includes(filterType)) {
          showPost = false;
        } else if (filterType.startsWith('tag-') && !tags.includes(filterType)) {
          showPost = false;
        }
      }
      
      // Apply search filter
      if (showPost && searchTerm) {
        if (!title.includes(searchTerm)) {
          showPost = false;
        }
      }
      
      // Show or hide the post
      if (showPost) {
        post.style.display = 'block';
        visiblePosts++;
      } else {
        post.style.display = 'none';
      }
    });
    
    // Show no results message if needed
    if (visiblePosts === 0) {
      noResults.style.display = 'block';
    } else {
      noResults.style.display = 'none';
    }
  }
</script>