---
title: PayEx Open Source Repositories
active_modules:
- PayEx.Checkout.WooCommerce
- PayEx.Psp.WooCommerce
legacy_modules:
- PayEx.Magento
- PayEx.Magento2
- PayEx.EPi.Commerce.Payment
- PayEx.PrestaShop
inactive_modules:
- PayEx.OpenCart
- PayEx.OpenCart2
- PayEx.WPeCommerce
- PayEx.Ubercart
libraries:
- PayEx.Ecommerce.Php
- django-payex
- pypayex
---

{% comment %}
TODO: Figure out why repository.archived always returns false, even for archived repositories.
TODO: Figure out why repository.topics is empty for all repositories.
TODO: When the above has a solution, use 'archived' and 'topics' to classify repositories instead of front matter variables
{% endcomment %}

## Modules

{% for repository in site.github.public_repositories %}
  {% if page.active_modules contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

## Libraries and SDKs

{% for repository in site.github.public_repositories %}
  {% if page.libraries contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

{% assign excluded = page.legacy_modules | concat: page.inactive_modules | concat: page.inactive_modules | concat: page.libraries %}

## Other 

{% for repository in site.github.public_repositories %}
  {% unless excluded contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endunless %}
{% endfor %}

## Legacy Modules

{% for repository in site.github.public_repositories %}
  {% if page.legacy_modules contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

## Archived Modules

{% for repository in site.github.public_repositories %}
  {% if page.inactive_modules contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}
