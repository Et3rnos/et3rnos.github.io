---
title: Main Page
---

## Recent Posts
<ul>
{% assign first_posts = site.posts | slice:0, 3 %}
{% for post in first_posts %}
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

## Programming Posts
<ul>
{% for post in site.posts %}
    {% for pc in post.categories %}
      {% if pc == "programming" %}
		{% for tag in post.tags %}
		  {% if tag == "none" %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
		  {% endif %}
		{% endfor %}
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>
### TI-BASIC
<ul>
  {% for post in site.posts %}
    {% for pc in post.categories %}
      {% if pc == "programming" %}
		{% for tag in post.tags %}
		  {% if tag == "ti-basic" %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
		  {% endif %}
		{% endfor %}
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>

## Hacking Posts
<ul>
  {% for post in site.posts %}
    {% for pc in post.categories %}
      {% if pc == "hacking" %}
		{% for tag in post.tags %}
		  {% if tag == "none" %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
		  {% endif %}
		{% endfor %}
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>
### CTF Writeups
<ul>
  {% for post in site.posts %}
    {% for pc in post.categories %}
      {% if pc == "hacking" %}
		{% for tag in post.tags %}
		  {% if tag == "ctf-writeup" %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
		  {% endif %}
		{% endfor %}
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>