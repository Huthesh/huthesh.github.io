---
title: Kubernetes
layout: default
description: huthesh.github.io
categories: [Kubernetes]
permalink: /Kubernetes
---
<div class="container margintop">
<h1>Kubernetes</h1>
<br>
<div class="well well-lg">
{% for category in site.categories %}
    {% if category[0]=="Kubernetes"%}
      {% for post in category[1] %}
        {% if post.title != "Kubernetes" %}
        <br>
        <li><a class="hlink" href="{{ post.url }}">{{ post.title }}</a></li>
        {% endif %}
      {% endfor %}
    {% endif %}
{% endfor %}
</div>
</div>
