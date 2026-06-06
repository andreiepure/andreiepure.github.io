---
layout: home
title: Home
---

<section class="hero">
  <p class="hero__label">Engineering Manager</p>
  <h1 class="hero__name">Andrei Epure</h1>
  <p class="hero__tagline">I help product engineering teams deliver reliable systems, with a strong technical voice and customer empathy.</p>
  <div class="hero__cta">
    <a class="btn-primary" href="{{ '/impact/' | relative_url }}">Selected work</a>
    <a class="btn-secondary" href="{{ '/about/' | relative_url }}">About me</a>
  </div>
</section>

<section class="home-impact">
  <p class="section-label">Impact</p>
  <ul class="impact-preview-list">
    {% for item in site.data.impact %}
    <li><a href="{{ '/impact/' | relative_url }}">{{ item.title }}</a></li>
    {% endfor %}
  </ul>
  <a class="home-more-link" href="{{ '/impact/' | relative_url }}">View all work &rarr;</a>
</section>

<div class="home-columns">
  <section>
    <p class="section-label">Speaking</p>
    <ul class="home-column-list">
      {% assign featured_talk = site.data.talks | where: "featured", true | first %}
      {% if featured_talk %}
      <li>
        <a href="{{ '/speaking/' | relative_url }}">{{ featured_talk.title }}</a>
        <span class="list-meta">{{ featured_talk.event }}, {{ featured_talk.date | split: "-" | first }}</span>
      </li>
      {% endif %}
      {% assign other_talks = site.data.talks | where: "featured", false %}
      {% for talk in other_talks limit:2 %}
      <li>
        <a href="{{ '/speaking/' | relative_url }}">{{ talk.event }}</a>
        <span class="list-meta">{{ talk.date | split: "-" | first }}</span>
      </li>
      {% endfor %}
    </ul>
    <a class="home-more-link" href="{{ '/speaking/' | relative_url }}">All talks &rarr;</a>
  </section>

  <section>
    <p class="section-label">Writing</p>
    <ul class="home-column-list">
      {% for post in site.posts limit:3 %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        <span class="list-meta">{{ post.date | date: "%Y" }}</span>
      </li>
      {% endfor %}
    </ul>
    <a class="home-more-link" href="{{ '/writing/' | relative_url }}">All posts &rarr;</a>
  </section>
</div>

<section class="home-about">
  <p class="section-label">About</p>
  <p>Engineering Manager at <a href="https://www.sonarsource.com/">Sonar</a> in Switzerland, currently leading the Integrations Squad. I've spent the last several years bridging product, engineering, and customer-facing work: most recently on the connectors that make SonarQube Cloud usable at enterprise scale.</p>
  <a class="home-more-link" href="{{ '/about/' | relative_url }}">More about me &rarr;</a>
</section>

<section class="home-contact">
  <p class="section-label">Contact</p>
  <p>The best way to reach me is via LinkedIn.</p>
  <div class="contact-links">
    <a href="https://www.linkedin.com/in/epureandrei/" rel="noopener">LinkedIn</a>
    <a href="https://github.com/andreiepure" rel="noopener">GitHub</a>
    <a href="https://sessionize.com/andrei-epure/" rel="noopener">Sessionize</a>
  </div>
</section>
