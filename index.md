---
title: PayEx Open Source Repositories
active_modules:
- PayEx.Checkout.WooCommerce
- PayEx.Psp.WooCommerce
legacy:
- PayEx.Magento
- PayEx.Magento2
- PayEx.EPi.Commerce.Payment
- PayEx.WooCommerce
- PayEx.PrestaShop
- PayEx.OpenCart2
- django-payex
- pypayex
libraries:
- PayEx.Ecommerce.Php
---

{% comment %}
TODO: Figure how to retrieve repository.topics for all repositories and use it to classify repositories instead of front matter variables. Related: https://developer.github.com/v3/repos/#list-all-topics-for-a-repository
{% endcomment %}

{% assign active_repositories = site.github.public_repositories | where: 'archived', false %}
{% assign archived_repositories = site.github.public_repositories | where: 'archived', true %}
{% assign excluded = page.legacy | concat: page.libraries | concat: page.active_modules %}

Here you will find PayEx' open source repositories. They should all be written according to
[PayEx Open Source Development Guidelines][1].

## Modules

Actively maintained modules, plugins and extensions for web shop platforms such as WooCommerce and Magento.

{% for repository in active_repositories %}
  {% if page.active_modules contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

## Libraries and SDKs

Actively maintained libraries and SDKs for PayEx' API platform.

{% for repository in active_repositories %}
  {% if page.libraries contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

## Other 

Other open source repositories hosted by PayEx, such as the PayEx Design Guide, etc.

{% for repository in active_repositories %}
  {% unless excluded contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endunless %}
{% endfor %}

## Legacy

These legacy modules, libraries and SDKs integrate against PayEx' old SOAP-based eCommerce-platform commonly referred to as "POPS".

{% for repository in active_repositories %}
  {% if page.legacy contains repository.name %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
  {% endif %}
{% endfor %}

## Archive

These repostories are archived and no longer maintained by PayEx.

{% for repository in archived_repositories %}
  * [{{ repository.name }}]({{ repository.html_url }}): {{ repository.description }}
{% endfor %}

[1]: https://developer.payex.com/xwiki/wiki/developer/view/Main/guidelines/open-source-development-guidelines/