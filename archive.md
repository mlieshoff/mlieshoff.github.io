---
layout: page
title: Archive
---

> "The happiness of your life depends upon the quality of your thoughts."
> 
> ―Marcus Aurelius, Meditations

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
