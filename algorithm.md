---
layout: page
title: Algorithm
---

{% assign tags = "" %}

{% for post in site.posts %}
  {% if post.tag1 == "Algorithm" %}
  {% if post.tag2 != "" %}
    {% if tags == "" %}
    {% assign tags = post.tag2 | split:'|' %}
    {% endif %}
  {% unless tags contains post.tag2 %}
    {% assign tags = tags | join:'|' | append:'|' | append:post.tag2 | split:'|' %}
  {% endunless %}
  {% endif %}
  {% endif %}
{% endfor %}

{% for tag in tags %}
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
