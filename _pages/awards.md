---
title: "Honors and awards"
permalink: /awards/
no_prose: true
---
{% assign grad = site.data.awards | where: "stage", "graduate" %}
{% assign ug = site.data.awards | where: "stage", "undergraduate" %}
<div class="prose">
  <section class="cv-section">
    <h2>Graduate studies, Oakland University</h2>
    {% include nv-award-rows.html items=grad %}
  </section>
  <section class="cv-section">
    <h2>Undergraduate studies, Ho Chi Minh City University of Education</h2>
    {% include nv-award-rows.html items=ug %}
  </section>
</div>
