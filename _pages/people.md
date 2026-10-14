---
title: "People"
permalink: /people/
layout: single
hide_footer: true
---

{% include base_path %}

{% for group in site.data.people %}
<section class="member-section">
  <h2 class="section-title">{{ group.section }}</h2>
  <div class="member-list">
    {% for p in group.people %}
      {% include member-card.html person=p %}
    {% endfor %}
  </div>
</section>
{% endfor %}

<section class="member-section">
  <h2 class="section-title">Join Us</h2>
  <p>We are recruiting PhD students, postdocs, and visiting scholars. See <a href="{{ base_path }}/opportunities/">Join Us</a>.</p>
</section>
