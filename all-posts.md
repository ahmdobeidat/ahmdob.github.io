---
layout: default
title: جميع المقالات
permalink: /all-posts/
lang: ar
---

<h1>جميع المقالات</h1>

<div class="view-toggle">
  <button onclick="setView('grid')" id="grid-btn" class="active">عرض شبكي</button>
  <button onclick="setView('list')" id="list-btn">عرض قائمة</button>
</div>

<div id="posts" class="grid-view">
  {% for post in site.posts %}
    <div class="post-card">
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt | strip_html | truncate: 150 }}</p>
      <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    </div>
  {% endfor %}
</div>

<script>
function setView(view) {
  const postsContainer = document.getElementById('posts');
  const gridBtn = document.getElementById('grid-btn');
  const listBtn = document.getElementById('list-btn');
  
  // Update container class
  postsContainer.className = view + '-view';
  
  // Update button states
  if (view === 'grid') {
    gridBtn.classList.add('active');
    listBtn.classList.remove('active');
  } else {
    listBtn.classList.add('active');
    gridBtn.classList.remove('active');
  }
}
</script>

<style>
.view-toggle {
  margin-bottom: 2em;
  text-align: center;
}

.view-toggle button {
  background: #f1f1f1;
  border: 1px solid #ddd;
  padding: 0.5em 1em;
  margin: 0 0.25em;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.view-toggle button:hover {
  background: #e1e1e1;
}

.view-toggle button.active {
  background: #007cba;
  color: white;
  border-color: #007cba;
}

#posts.grid-view {
  display: flex;
  flex-wrap: wrap;
  gap: 1em;
  margin-top: 1em;
}

#posts.grid-view .post-card {
  width: calc(33.333% - 0.67em);
  border: 1px solid #ccc;
  padding: 1em;
  box-sizing: border-box;
  border-radius: 4px;
  background: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

#posts.list-view {
  display: block;
  margin-top: 1em;
}

#posts.list-view .post-card {
  width: 100%;
  border-bottom: 1px solid #ccc;
  padding: 1em 0;
  background: transparent;
  box-shadow: none;
  border-radius: 0;
}

.post-card h2 {
  margin-top: 0;
  margin-bottom: 0.5em;
}

.post-card h2 a {
  text-decoration: none;
  color: inherit;
}

.post-card h2 a:hover {
  color: #007cba;
}

.post-card p {
  margin: 0.5em 0;
  line-height: 1.5;
}

.post-date {
  font-size: 0.9em;
  color: #666;
  font-style: italic;
}

/* Responsive design */
@media (max-width: 768px) {
  #posts.grid-view .post-card {
    width: calc(50% - 0.5em);
  }
}

@media (max-width: 480px) {
  #posts.grid-view .post-card {
    width: 100%;
  }
}

/* Dark theme support */
@media (prefers-color-scheme: dark) {
  #posts.grid-view .post-card {
    background: #1e1e1e;
    border-color: #444;
    color: #fff;
  }
  
  .view-toggle button {
    background: #333;
    border-color: #555;
    color: #fff;
  }
  
  .view-toggle button:hover {
    background: #444;
  }
}
</style>