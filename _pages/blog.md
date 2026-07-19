---
layout: default
permalink: /blog/
title: Blog
nav: true
nav_order: 1
pagination:
  enabled: false # all posts on one page so the topic filter works across the whole blog (Gundersen-style)
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3 # The number of links after the current page
---

<style>
/* Blog: smaller, minimalistic header + tighter post list (matches the home page) */
.header-bar { text-align: left; padding: 1.25rem 0 0.5rem; border-bottom: none; margin-bottom: 0; }
.header-bar h1 { font-size: 2rem; margin-bottom: 0.15rem; }
.header-bar h2 { font-size: 1.05rem; font-weight: 400; opacity: 0.7; margin-bottom: 0; }
/* Topic filter row (Gundersen-style): click a topic to filter the list in place */
.topic-filter { display: flex; flex-wrap: wrap; gap: 0.35rem 1.1rem; margin: 0.85rem 0 2.25rem; }
.topic-filter a { font-size: 0.95rem; color: var(--global-text-color); opacity: 0.55; text-decoration: none; cursor: pointer; transition: opacity .15s ease, color .15s ease; }
.topic-filter a:hover { opacity: 1; color: var(--global-theme-color); }
.topic-filter a.active { opacity: 1; color: var(--global-theme-color); }
.post-list { margin-top: 0.5rem; }
.post-list .post-title { font-size: 1.3rem; font-weight: 400; }
.post-list li { margin-bottom: 1.75rem; line-height: 1.6; }
.post-list .post-meta { margin: 0; opacity: 0.7; font-size: 0.9rem; }
</style>

<div class="post">

{% assign blog_name_size = site.blog_name | size %}
{% assign blog_description_size = site.blog_description | size %}

{% if blog_name_size > 0 or blog_description_size > 0 %}

  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>
  {% endif %}

{% if site.display_tags and site.display_tags.size > 0 or site.display_categories and site.display_categories.size > 0 %}

  <nav class="topic-filter">
    <a data-topic="__all__" class="active">All</a>
    {% for tag in site.display_tags %}
      <a data-topic="{{ tag | slugify }}">{{ tag }}</a>
    {% endfor %}
    {% for category in site.display_categories %}
      <a data-topic="{{ category | slugify }}">{{ category }}</a>
    {% endfor %}
  </nav>
  {% endif %}

{% assign featured_posts = site.posts | where: "featured", "true" %}
{% if featured_posts.size > 0 %}
<br>

<div class="container featured-posts">
{% assign is_even = featured_posts.size | modulo: 2 %}
<div class="row row-cols-{% if featured_posts.size <= 2 or is_even == 0 %}2{% else %}3{% endif %}">
{% for post in featured_posts %}
<div class="col mb-4">
<a href="{{ post.url | relative_url }}">
<div class="card hoverable">
<div class="row g-0">
<div class="col-md-12">
<div class="card-body">
<div class="float-right">
<i class="fa-solid fa-thumbtack fa-xs"></i>
</div>
<h3 class="card-title text-lowercase">{{ post.title }}</h3>
<p class="card-text">{{ post.description }}</p>

                    {% if post.external_source == blank %}
                      {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
                    {% else %}
                      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
                    {% endif %}
                    {% assign year = post.date | date: "%Y" %}

                    <p class="post-meta">
                      {{ read_time }} min read &nbsp; &middot; &nbsp;
                      <a href="{{ year | prepend: '/blog/' | prepend: site.baseurl}}">
                        <i class="fa-solid fa-calendar fa-sm"></i> {{ year }} </a>
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </a>
        </div>
      {% endfor %}
      </div>
    </div>
    <hr>

{% endif %}

  <ul class="post-list">

    {% if page.pagination.enabled %}
      {% assign postlist = paginator.posts %}
    {% else %}
      {% assign postlist = site.posts %}
    {% endif %}

    {% for post in postlist %}

    {% if post.external_source == blank %}
      {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
    {% else %}
      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% endif %}
    {% assign year = post.date | date: "%Y" %}
    {% assign topic_slugs = '' %}
    {% for t in post.tags %}{% assign ts = t | slugify %}{% assign topic_slugs = topic_slugs | append: ts | append: ' ' %}{% endfor %}
    {% for c in post.categories %}{% assign cs = c | slugify %}{% assign topic_slugs = topic_slugs | append: cs | append: ' ' %}{% endfor %}

    <li data-tags="{{ topic_slugs | strip }}">

{% if post.thumbnail %}

<div class="row">
          <div class="col-sm-9">
{% endif %}
        <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% elsif post.redirect contains '://' %}
          <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
          <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
            <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
          </svg>
        {% else %}
          <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </h3>
      <p>{{ post.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read &nbsp; &middot; &nbsp;
        {{ post.date | date: '%B %d, %Y' }}
        {% if post.external_source %}
        &nbsp; &middot; &nbsp; {{ post.external_source }}
        {% endif %}
      </p>
{% if post.thumbnail %}

</div>

  <div class="col-sm-3">
    <img class="card-img" src="{{ post.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="image">
  </div>
</div>
{% endif %}
    </li>

    {% endfor %}

  </ul>

{% if page.pagination.enabled %}
{% include pagination.liquid %}
{% endif %}

</div>

<script>
  (function () {
    var controls = document.querySelectorAll('.topic-filter [data-topic]');
    var posts = document.querySelectorAll('.post-list > li');
    function apply(topic) {
      controls.forEach(function (el) {
        el.classList.toggle('active', el.dataset.topic === topic);
      });
      posts.forEach(function (li) {
        var tags = (li.dataset.tags || '').split(/\s+/);
        var show = topic === '__all__' || tags.indexOf(topic) !== -1;
        li.style.display = show ? '' : 'none';
      });
    }
    controls.forEach(function (el) {
      el.addEventListener('click', function (e) {
        e.preventDefault();
        var t = el.dataset.topic;
        if (t !== '__all__' && el.classList.contains('active')) t = '__all__';
        apply(t);
      });
    });
    apply('__all__');
  })();
</script>
