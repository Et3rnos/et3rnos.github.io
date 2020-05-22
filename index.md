## Recent Posts
{% for post in site.posts %}
<ul>
	<li><a href="{{ post.url }}">{{ post.title }}</a></li>
</ul>
{% endfor %}

{% for cat in site.category-list %}
## {{ cat | capitalize }} Posts
<ul>
  {% for post in site.posts %}
    {% for pc in post.categories %}
      {% if pc == cat %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>
{% endfor %}