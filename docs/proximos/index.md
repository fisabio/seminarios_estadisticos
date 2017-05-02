---
layout: page
title: Próximos Seminarios
excerpt: "Aquí verás los próximos seminarios que se celebrarán"
search_omit: true
---

<ul class="post-list">
{% for post in site.categories.proximos %}
  <li>
    <article>
      <a href="{{ site.url }}{{ post.url }}">{{ post.title }}
        <span class="entry-date">
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {% assign m = post.date | date: "%-m" %}
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
            {{ post.date | date: "%Y" }}
          </time>
        </span>
        {% if post.excerpt %}
          <span class="excerpt">
            {{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}
          </span>
        {% endif %}
      </a>
    </article>
  </li>
{% endfor %}
</ul>
