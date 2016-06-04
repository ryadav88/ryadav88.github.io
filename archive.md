<!-- ---
layout: page
title: Archive
---

## Blog Posts

{% for post in site.posts %}
{% include readingtime.html %}
###  [{{ post.title }}]({{ post.url }}) <br/>
  <span class="post-date">{{ post.date | date: "%B %e, %Y" }} • {{ reading_time }} read</span>
  <p>{{ post.excerpt | remove: '<p>' | remove: '</p>' | strip_html | truncate: 150 }}</p>
  ***
{% endfor %} -->
