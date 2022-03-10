---
title: "AWS SDK for .NET"
date: 2021-11-03T08:00:00-07:00
categories:
  - blog
tags:
  - aws
  - aws-sdk-dot-net
  - asp-net-core
  - clean-architecture
---
{% assign sorted_posts = site.website_hosted_on_s3 | sort: "position" %}

{% for page in sorted_posts %}
  <h3>
    <a href="{{ page.url }}">
      {{ page.title }}
    </a>
  </h3>
{% endfor %}