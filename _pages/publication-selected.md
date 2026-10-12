---
title: "Publications"
permalink: /publication/selected/
layout: single
hide_footer: true
---

{% include base_path %}

<div class="pub-tabs">
  <a class="is-active" href="{{ base_path }}/publication/selected/">Selected</a>
  <a href="{{ base_path }}/publication/all/">All</a>
</div>

{% assign featured = site.data.publications | where: "selected", true %}
{% for p in featured %}
  {% include pub-item.html pub=p card=true %}
{% endfor %}
