---
title: Swedbank Pay Open Source Repositories
libraries:
- swedbank-pay-sdk-android
- swedbank-pay-sdk-ios
---

{% comment %}
TODO: Figure how to retrieve repository.topics for all repositories and use it to classify repositories instead of front matter variables. Related: https://developer.github.com/v3/repos/#list-all-topics-for-a-repository
{% endcomment %}

{% assign active_repositories = site.github.public_repositories | where: 'archived', false %}
{% assign excluded = page.libraries %}

Here you will find Swedbank Pay's open source repositories. They should all be
written according to [PayEx Open Source Development Guidelines][1].

## Libraries and SDKs

Actively maintained libraries and SDKs for Swedbank Pay' API platform.

{% for repository in active_repositories %}
  {% if page.libraries contains repository.name %}
  * [{{repository.description}}]({{ repository.html_url }})
  {% endif %}
{% endfor %}

## Other

Other open source repositories hosted by Swedbank Pay, such as the Swedbank Pay
Design Guide, etc.

{% for repository in active_repositories %}
  {% unless excluded contains repository.name %}
  * [{{ repository.description }}]({{ repository.html_url }})
  {% endunless %}
{% endfor %}


[1]: https://developer.payex.com/xwiki/wiki/developer/view/Main/guidelines/open-source-development-guidelines/
