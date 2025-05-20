---
title: People
permalink: /people/
---

页面共抓到 {{ site.people | size }} 条成员。

<ul>
{% for p in site.people %}
  <li>{{ p.name }} — joined: {{ p.joined }}</li>
{% endfor %}
</ul>
