## My Posts
{% for post in site.posts %}
[{{post.title}}]({{post.url}})
```{{post.content | strip_html | truncate: 100 }}```
{% endfor %}