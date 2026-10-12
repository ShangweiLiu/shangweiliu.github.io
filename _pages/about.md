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
  <p class="hero__lead">We combine system modeling and economic analysis to inform decision-making in net-zero energy transitions, climate policy, and industrial policy.</p>
</section>

<section class="home-section home-section--first">
  <h2 class="section-title">Research</h2>
  <!-- Photos live in images/research/ (CC0 / public domain, from Wikimedia Commons); replace a file to change its picture. -->
  <div class="card-grid card-grid--3">
    <div class="card card--media">
      <img class="card__media" src="{{ base_path }}/images/research/energy-system-modeling.jpg" alt="Electricity pylons at sunset" loading="lazy">
      <div class="card__body">
        <p class="card__kicker">Area 01</p>
        <h3>Energy System Modeling</h3>
        <p>Designing pathways to net-zero energy systems across sectors, including power, heating, buildings, and industry.</p>
      </div>
    </div>
    <div class="card card--media">
      <img class="card__media" src="{{ base_path }}/images/research/technology-innovation.jpg" alt="Looking up through a nuclear cooling tower" loading="lazy">
      <div class="card__body">
        <p class="card__kicker">Area 02</p>
        <h3>Technology Innovation</h3>
        <p>Costs and deployment of low-carbon technologies such as nuclear power and hydrogen, and the industrial policies that shape them.</p>
      </div>
    </div>
    <div class="card card--media">
      <img class="card__media" src="{{ base_path }}/images/research/climate-change-impacts.jpg" alt="Satellite map of urban heat in Paris" loading="lazy">
      <div class="card__body">
        <p class="card__kicker">Area 03</p>
        <h3>Climate Change Impacts</h3>
        <p>The distributional impacts of climate change on individuals and nations.</p>
      </div>
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
  {% comment %}Home page shows only the selected Nature-family papers, three across.{% endcomment %}
  {% assign featured = site.data.publications | where: "selected", true | where_exp: "p", "p.venue contains 'Nature'" %}
  <div class="pub-tiles">
    {% for p in featured limit: 3 %}
      {% include pub-item.html pub=p tile=true %}
    {% endfor %}
  </div>
  <p><a class="more-link" href="{{ base_path }}/publication/all/">All publications →</a></p>
</section>

<section class="cta">
  <div>
    <h2>Join the group</h2>
    <p>We are recruiting PhD students (Fall 2027), postdocs, and visiting scholars.</p>
  </div>
  <a class="btn-pill btn-pill--accent" href="{{ base_path }}/opportunities/">See opportunities</a>
</section>
