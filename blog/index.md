---
layout: home # Or 'page', or a custom layout for your blog index
title: Blog Posts
permalink: /blog/ # This is crucial to make this page accessible at /blog/
---

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h2>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h2>
      {% if site.show_excerpts %}
        {{ post.excerpt }}
      {% endif %}
      <p><a href="{{ post.url | relative_url }}">Read more</a></p>
    </li>
  {% endfor %}
</ul>

{% if paginator.total_pages > 1 %}
  <div class="pagination">
    {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path | relative_url }}" class="previous">Previous</a>
    {% endif %}
    {% for page in (1..paginator.total_pages) %}
      <a href="{{ paginator.page_path | relative_url | replace: ':num', page }}" {% if page == paginator.page %}class="active"{% endif %}>{{ page }}</a>
    {% endfor %}
    {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path | relative_url }}" class="next">Next</a>
    {% endif %}
  </div>
{% endif %}