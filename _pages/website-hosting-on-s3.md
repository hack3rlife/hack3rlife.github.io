---
title: "Hosting a static website on Amazon S3"
permalink: "/website_hosted_on_s3/"
---
{% assign sorted_posts = site.website_hosted_on_s3 | sort: "position" %}

{% for page in sorted_posts %}
  <p>
    <a href="{{ page.url }}">
      {{ page.title }}
    </a>
  </p>
{% endfor %}