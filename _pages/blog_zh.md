---
layout: default
permalink: /zh/blog/
title: 博客
nav: False
nav_order: 1
locale: zh
translation_key: blog-index
blog_name: 博客
blog_description: Aiden 的学术与个人记录。
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---

{% include blog_index.liquid %}
