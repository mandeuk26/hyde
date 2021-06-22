---
layout: page
title: Algorithm
---

{% assign tags = "" | split: ',' %}

{% for post in site.posts %}
  {% if post.tags contains "Algorithm" %}

​	{% for tag in post.tags %}

{% if tag != "Algorithm" %}

  {% unless tags contains tag %}
    {% assign tags = tags | push: tag %}
  {% endunless %}
  {% endif %}

{% endfor %}

  {% endif %}
{% endfor %}

{% for tag in tags | reverse %}
<p id="{{ tag | slugify }}"><b>{{ tag }}</b></p>
<ul>
  {% for post in site.posts | reverse %}
  {% if post.tags contains "Algorithm" %}
  {% if post.tags contains tag %}
  <li>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
  </li>
  {% endif %}
  {% endif %}
  {% endfor %}
</ul>


{% endfor %}
