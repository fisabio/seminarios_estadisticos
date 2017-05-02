---
layout: page
title: Etiquetas
search_omit: true
---

{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}

<ul class="tag-box inline">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
    <li><a href="#{{ this_word }}">{{ this_word }} <span>{{ site.tags[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  <h2 id="{{ this_word }}">{{ this_word }}</h2>
  <ul class="post-list">
  {% for post in site.tags[this_word] %}{% if post.title != null %}
    <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}<span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% assign m = post.date | date: "%-m" %}
    {{ post.date | date: "%-d de" }}
    {% case m %}
      {% when '1' %}Enero,
      {% when '2' %}Febrero,
      {% when '3' %}Marzo,
      {% when '4' %}Abril,
      {% when '5' %}Mayo,
      {% when '6' %}Junio,
      {% when '7' %}Julio,
      {% when '8' %}Agosto,
      {% when '9' %}Septiembre,
      {% when '10' %}Octubre,
      {% when '11' %}Noviembre,
      {% when '12' %}Diciembre,
    {% endcase %}
    {{ post.date | date: "%Y" }}</time></span></a></li>
  {% endif %}{% endfor %}
  </ul>
{% endunless %}{% endfor %}
