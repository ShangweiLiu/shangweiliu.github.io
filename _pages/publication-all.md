---
title: "Publications"
permalink: /publication/all/
layout: single
hide_footer: true
---

{% include base_path %}

<div class="pub-tabs">
  <a href="{{ base_path }}/publication/selected/">Selected</a>
  <a class="is-active" href="{{ base_path }}/publication/all/">All</a>
</div>

<p class="pub-scholar">For the most up-to-date list, see <a href="https://scholar.google.com/citations?user=PxXSclcAAAAJ&hl=en">Google Scholar</a>.</p>

{% assign by_year = site.data.publications | group_by: "year" %}
{% for y in by_year %}
<section class="pub-year">
  <h2 class="pub-year__label">{{ y.name }}</h2>
  <div class="pub-year__items">
    {% for p in y.items %}
      {% include pub-item.html pub=p %}
    {% endfor %}
  </div>
</section>
{% endfor %}
