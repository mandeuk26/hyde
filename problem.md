---
layout: page
title: Problem
---

{% assign tags = "" | split: ',' %}

{% for post in site.posts reversed %}
  {% if post.tags contains "Problem" %}
    {% for tag in post.tags %}
      {% if tag != "Problem" %}
        {% unless tags contains tag %}
          {% assign tags = tags | push: tag %}
        {% endunless %}
      {% endif %}
    {% endfor %}
  {% endif %}
{% endfor %}

{% for tag in tags %}

<p id="{{ tag | slugify }}"><b>{{ tag }}</b></p>
<ul>
  {% for post in site.posts reversed %}
  {% if post.tags contains tag %}
  {% if post.tags contains "Problem" %}
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
