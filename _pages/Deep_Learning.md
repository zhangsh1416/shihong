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

<div class="navigation">
  {% for category in site.data.deep_learning.navigation %}
  {% capture category_title %}## {{ category.title }}{% endcapture %}
  {{ category_title | markdownify }}
  <div class="subcategories">
    {% for subcategory in category.subcategories %}
    <div class="subcategory">
      {% capture subcategory_title %}### {{ subcategory.title }}{% endcapture %}
      {{ subcategory_title | markdownify }}
      <ul class="links">
        {% for link in subcategory.links %}
         <li><a href="{{ link.url | relative_url }}">{{ link.title }}</a></li>
        {% endfor %}
      </ul>
    </div>
    {% endfor %}
  </div>
  {% endfor %}
</div>