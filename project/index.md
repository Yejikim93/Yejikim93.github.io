---
layout: default
work: true
main: true
title: My Projects
description: About complete & on-going Project (진행중 & 완료한 프로젝트 정리)  
project-header: true
header-img: "img/project_bg.jpg"
---

<div class="catalogue">
{% assign sorted = site.pages | sort: 'order' | reverse %}
{% for page in sorted %}
{% if page.projects == true %}

     {% include post-list.html %}

{% endif %}
{% endfor %}
</div>
