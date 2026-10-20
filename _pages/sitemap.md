---
title: "Sitemap"
permalink: /sitemap/
no_prose: true
---
<div class="prose">
  <section class="cv-section">
    <h2>Pages</h2>
    <ul>
      {% for link in site.data.navigation.main %}<li><a href="{{ link.url | relative_url }}">{{ link.title }}</a></li>{% endfor %}
      <li><a href="{{ '/research/newton-methods/' | relative_url }}">Newton-type methods for nonsmooth optimization</a></li>
      <li><a href="{{ '/awards/' | relative_url }}">Honors and awards</a></li>
      <li><a href="{{ '/portfolio/' | relative_url }}">Computing projects</a></li>
    </ul>
  </section>
  <section class="cv-section">
    <h2>Papers</h2>
    <ul>
      {% assign pubs = site.publications | where_exp: "p", "p.cv_order" | sort: "cv_order" %}
      {% for post in pubs %}<li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>{% endfor %}
    </ul>
  </section>
  <p class="meta">An <a href="{{ '/sitemap.xml' | relative_url }}">XML sitemap</a> is also available.</p>
</div>
