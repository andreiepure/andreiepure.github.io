---
layout: page
title: Speaking
permalink: /speaking/
description: "Andrei Epure's conference talks on .NET software supply chain security, dependency confusion, and NuGet security."
---

<h1>Speaking</h1>

<p class="page-intro">I speak on .NET software supply chain security and developer tooling at conferences across Europe and online. My <a href="https://sessionize.com/andrei-epure/">Sessionize profile</a> has the full list.</p>

{% assign featured_talks = site.data.talks | where: "featured", true %}
{% if featured_talks.size > 0 %}
{% for talk in featured_talks %}
<div class="talk-featured">
  <h2>{{ talk.title }}</h2>
  <p class="talk-meta">{{ talk.event }} &middot; {{ talk.location }} &middot; {{ talk.date | split: "-" | first }}</p>
  <p class="talk-links">
    {% if talk.recording_url != "" and talk.recording_url %}<a href="{{ talk.recording_url }}" rel="noopener">Watch recording &rarr;</a>{% endif %}
    {% if talk.url != "" and talk.url %}{% if talk.recording_url != "" and talk.recording_url %} &middot; {% endif %}<a href="{{ talk.url }}" rel="noopener">Slides</a>{% endif %}
  </p>
</div>
{% endfor %}
{% endif %}

<h2>All talks</h2>

<table class="talks-table">
  <thead>
    <tr>
      <th>Date</th>
      <th>Event</th>
      <th>Talk</th>
      <th>Resources</th>
    </tr>
  </thead>
  <tbody>
    {% for talk in site.data.talks %}
    <tr>
      <td class="talk-date">{{ talk.date }}</td>
      <td>{{ talk.event }}, {{ talk.location }}</td>
      <td>{{ talk.title }}</td>
      <td>
        {% if talk.recording_url != "" and talk.recording_url %}<a href="{{ talk.recording_url }}" rel="noopener">Recording</a>{% endif %}
        {% if talk.url != "" and talk.url %}{% if talk.recording_url != "" and talk.recording_url %} · {% endif %}<a href="{{ talk.url }}" rel="noopener">Slides</a>{% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>
