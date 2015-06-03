---
layout: page
title: Archive
header-img: "img/archive-bg.jpg"
---

## Blog posts

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}
