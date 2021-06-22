---
layout: page
title: Algorithm
---

{% assign tags = "" | split: ',' %}

{% for post in site.posts %}
  {% if post.tag1 == "Algorithm" %}
  {% if post.tag2 != "" %}
  {% unless tags contains post.tag2 %}
    {% assign tags = tags | push: post.tag2 %}
  {% endunless %}
  {% endif %}
  {% endif %}
{% endfor %}

{% for tag in tags | reverse %}
<p id="{{ tag | slugify }}"><b>{{ tag }}</b></p>
<ul>
  {% for post in site.posts %}
  {% if post.tag1 == "Algorithm" %}
  {% if post.tag2 == tag %}
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
