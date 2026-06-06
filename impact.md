---
layout: page
title: Impact
permalink: /impact/
description: "Selected work from Andrei Epure — Engineering Manager at Sonar. From product launches to team growth."
---

<h1>Selected Work</h1>

<p class="page-intro">A selection of initiatives I led or co-led at Sonar. Focused on delivery outcomes, team capability, and customer impact.</p>

{% for item in site.data.impact %}
<div class="impact-item">
  <h2>{{ item.title }}</h2>
  <p class="impact-role">{{ item.role }}</p>
  <p>{{ item.description }}</p>
</div>
{% endfor %}
