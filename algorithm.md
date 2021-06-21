---
layout: page
title: Algorithm
---

{% assign rawtags = "" %}

{% for post in site.posts %}
  {% if post.tags contains "Algorithm" %}
  {% assign ttags = post.tags | join:'|' | append:'|' %}
  {% assign rawtags = rawtags | append:ttags %}
  {% endif %}
{% endfor %}

{% assign rawtags = rawtags | split:'|' | sort %}

{% assign tags = "" %}

{% for tag in rawtags %}
  {% if tag != "" && tag != "Algorithm" %}
    {% if tags == "" %}
    {% assign tags = tag | split:'|' %}
    {% endif %}
  {% unless tags contains tag %}
    {% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
  {% endunless %}
  {% endif %}
{% endfor %}

# Algorithm

{% for tag in tags %}
<p id="{{ tag | slugify }}"><b>{{ tag }}</b></p>
<ul>
  {% for post in site.posts %}
  {% if post.tags contains tag %}
  <li>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
  </li>
  {% endif %}
  {% endfor %}
</ul>
{% endfor %}

