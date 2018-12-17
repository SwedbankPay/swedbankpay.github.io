---
title: PayEx Open Source Repositories
active_modules:
- PayEx.Magento
- PayEx.Magento2
inactive_modules:
- PayEx.OpenCart
- PayEx.OpenCart2
---

{% for repository in site.github.public_repositories | where:'archived',false %}
  {% unless page.active_modules contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endunless %}
{% endfor %}