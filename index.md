---
title: PayEx Open Source Repositories
---

{% capture modules %}
A
B
C
D
{% endcapture %}

{% assign modules = modules | strip | newline_to_br | strip_newlines | split: "<br />" %}

{% for repository in site.github.public_repositories %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
{% endfor %}