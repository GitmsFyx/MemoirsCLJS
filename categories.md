---
layout: default
title: 文章合集
---

# 文章分类

以下是文章的分类。点击分类名称可快速跳转到对应文章列表。

<nav>
<ol>
{% assign sorted_categories = site.categories | sort %}
{% for category in sorted_categories %}
  <li><a href="#{{ category[0] | slugify }}">{{ category[0] | capitalize }} ({{ category[1].size }}篇)</a></li>
{% endfor %}
</ol>
</nav>

<hr/>

{% for category in sorted_categories %}
<section id="{{ category[0] | slugify }}">
  <h2>{{ category[0] | capitalize }}</h2>
  <ul>
    {% for post in category[1] %}
      <li>
        <a href="/MemoirsCLJS/{{ post.url }}">{{ post.title }}</a>
        <small>{{ post.date | date_to_string }}</small>
      </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}