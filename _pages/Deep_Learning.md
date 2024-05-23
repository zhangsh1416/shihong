---
layout: single
title: Deep Learning
permalink: /deep_learning
toc: true
toc_label: "Content"
toc_icon: "file"
toc_sticky: true      
---

# Welcome to the world of Deep Learning
{% for category in site.data.deep_learning.navigation %}
## {{ category.title }}
  {% for subcategory in category.subcategories %}
  - {{ subcategory.title }}
    {% for link in subcategory.links %}
    - [{{ link.title }}]({{ link.url | relative_url }})
    {% endfor %}
  {% endfor %}
{% endfor %}