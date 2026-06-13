---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign featured_pubs = site.publications | where: "featured", true | sort: "date" | reverse %}
{% assign other_pubs = site.publications | where_exp: "item", "item.featured != true" | sort: "date" | reverse %}

<h2 style="margin-top: 0;">Featured Publications</h2>
<div class="publications-grid">
{% for post in featured_pubs %}
  <div class="pub-grid-card">
    {% if post.header.teaser %}
      <div class="pub-card-image">
        <img src="{{ post.header.teaser | prepend: '/images/' | prepend: base_path }}" alt="">
      </div>
    {% endif %}
    <h3 class="pub-card-title"><a href="{{ base_path }}{{ post.url }}">{{ post.title }}</a></h3>
    <p class="pub-card-meta">
      Published in <i>{{ post.venue }}</i>, {{ post.date | date: "%Y" }}
    </p>
  </div>
{% endfor %}
</div>

<h3 style="margin-top: 3em; border-bottom: 1px solid rgba(0,0,0,0.1); padding-bottom: 0.5em;">Other Publications</h3>
<div class="other-publications-list">
{% for post in other_pubs %}
  <div class="other-pub-card">
    <div class="pub-title">
      <a href="{{ base_path }}{{ post.url }}">{{ post.title }}</a>
    </div>
    <div class="pub-meta">
      {% if post.citation %}
        {{ post.citation | split: '"' | first | strip }}<br>
      {% endif %}
      {% if post.venue %}
        Published in <i>{{ post.venue }}</i>, {{ post.date | date: "%Y" }}
      {% endif %}
    </div>
    <a href="{{ base_path }}{{ post.url }}" class="pub-link">Read more &rarr;</a>
  </div>
{% endfor %}
</div>
