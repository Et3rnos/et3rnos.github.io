## Recent Posts
{% for post in site.posts %}
[{{post.title}}]({{post.url}})
{% endfor %}

{% for cat in site.category-list %}
## {{ cat | capitalize }} Posts
<ul>
  {% for page in site.pages %}
    {% for pc in page.categories %}
      {% if pc == cat %}
        <li><a href="{{ page.url }}">{{ page.title }}</a></li>
      {% endif %}
    {% endfor %}
  {% endfor %}
</ul>
{% endfor %}