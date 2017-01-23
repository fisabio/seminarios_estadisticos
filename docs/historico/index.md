---
layout: page
title: Histórico de Seminarios
search_omit: true
---

Lo siento, pero todavía no ha habido ningún seminario, de modo que aún no hay nada que mostrar (aunque pronto lo habrá, paciencia...).

<ul class="post-list">
{% for post in site.categories.historico %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %d, %Y" }}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
