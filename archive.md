---
layout: page
title: Archive
---
<br />
{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})  

    {{ post.excerpt | strip_html }}
{% endfor %}
