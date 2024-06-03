---
layout: single
title: Papers
permalink: /papers
toc: true
toc_label: "Content"
toc_icon: "file"
toc_sticky: true
---

# Papers
<div class="navigation">
  {% for category in site.data.papers.navigation %}
  {{ category_title | markdownify }}
  <div class="subcategories">
    {% for subcategory in category.subcategories %}
       <div class="subcategory">
        {% capture subcategory_title %}### {{ subcategory.title }}{% endcapture %}
        {{ subcategory_title | markdownify }}
    <ul class="links">
      {% for link in subcategory.links %}
       <li>
         <a href="{{ link.url | relative_url }}">{{ link.title }}</a>
         <p>{{ link.description }}</p>
       </li>
      {% endfor %}
    </ul>
    {% endfor %}
  </div>
  {% endfor %}
</div>