---
layout: page
title: Impact
permalink: /impact/
description: "Selected work from Andrei Epure: Engineering Manager at Sonar. From product launches to team growth."
---

<h1>Selected Work</h1>

<p class="page-intro">A selection of initiatives I led or co-led at Sonar.</p>

{% assign sonar_impact = site.data.impact | where_exp: "item", "item.company == 'Sonar'" %}
{% for item in sonar_impact %}
<div class="impact-item">
  <h2>{{ item.title }}</h2>
  <p class="impact-role">{{ item.role }}</p>
  <p>{{ item.description }}</p>
</div>
{% endfor %}

<p class="page-intro">A selection of initiatives I led or co-led at Microsoft.</p>

{% assign microsoft_impact = site.data.impact | where_exp: "item", "item.company == 'Microsoft'" %}
{% for item in microsoft_impact %}
<div class="impact-item">
  <h2>{{ item.title }}</h2>
  <p class="impact-role">{{ item.role }}</p>
  <p>{{ item.description }}</p>
</div>
{% endfor %}
