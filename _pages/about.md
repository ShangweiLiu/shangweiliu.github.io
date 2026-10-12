---
permalink: /
title:
wide: true
hide_footer: true
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}

<section class="hero">
  <p class="hero__eyebrow">Department of Civil and Environmental Engineering · National University of Singapore</p>
  <h1 class="hero__title">{{ site.title }}</h1>
  <p class="hero__lead">We study energy and climate policy, combining engineering-based modeling with policy and economic analysis to inform the transition to net-zero energy systems.</p>
  <p class="hero__pi">Led by <a href="{{ base_path }}/people/">Dr. Shangwei Liu</a>, Presidential Fellow at NUS</p>
  <p class="hero__actions">
    <a class="btn-pill btn-pill--primary" href="{{ base_path }}/people/">Meet the group</a>
    <a class="btn-pill" href="{{ base_path }}/publication/selected/">Publications</a>
    <a class="btn-pill btn-pill--accent" href="{{ base_path }}/opportunities/">Join us</a>
  </p>
</section>

<section class="home-section">
  <h2 class="section-title">Research</h2>
  <div class="card-grid">
    <div class="card">
      <i class="fas fa-bolt card__icon" aria-hidden="true"></i>
      <h3>Clean energy transition</h3>
      <p>Pathways to net-zero energy systems across power, heating, and industry.</p>
    </div>
    <div class="card">
      <i class="fas fa-lightbulb card__icon" aria-hidden="true"></i>
      <h3>Technology innovation</h3>
      <p>Costs and deployment of low-carbon technologies such as nuclear power and hydrogen.</p>
    </div>
    <div class="card">
      <i class="fas fa-temperature-high card__icon" aria-hidden="true"></i>
      <h3>Climate change impacts</h3>
      <p>How climate extremes affect energy systems and who bears the consequences.</p>
    </div>
    <div class="card">
      <i class="fas fa-earth-asia card__icon" aria-hidden="true"></i>
      <h3>Southeast Asia</h3>
      <p>Decarbonization pathways in Southeast Asia and their environmental implications.</p>
    </div>
  </div>
</section>

{% if site.data.news.size > 0 %}
<section class="home-section">
  <h2 class="section-title">News</h2>
  <ul class="news">
    {% for item in site.data.news limit: 6 %}
      <li><time datetime="{{ item.date | date_to_xmlschema }}">{{ item.date | date: "%b %Y" }}</time><span>{{ item.text | markdownify | remove: "<p>" | remove: "</p>" | strip }}</span></li>
    {% endfor %}
  </ul>
</section>
{% endif %}

<section class="home-section">
  <h2 class="section-title">Selected Publications</h2>
  {% assign featured = site.data.publications | where: "selected", true %}
  {% for p in featured %}
    {% include pub-item.html pub=p card=true %}
  {% endfor %}
  <p><a class="more-link" href="{{ base_path }}/publication/all/">All publications →</a></p>
</section>

<section class="cta">
  <div>
    <h2>Join the group</h2>
    <p>We are recruiting PhD students (Fall 2027), postdocs, and visiting scholars.</p>
  </div>
  <a class="btn-pill btn-pill--accent" href="{{ base_path }}/opportunities/">See opportunities</a>
</section>
