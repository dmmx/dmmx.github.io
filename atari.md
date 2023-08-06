---
layout: page
title: Atari
permalink: /atari/
subject: atari
---

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'subject', page.subject %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>