---
layout: post
title:  "Binary Behaviour Analysis"
date:   2021-08-30 15:52:19 +0300
categories: report
index: true
---

# Generic Information
The conducted analysis attempts to automatically identify the behaviour of binaries by evaluating the implemented methods.
A list is presented below which includes mostly malicious samples.

# List of Samples
<ul>
{%- for post in site.posts -%}
    {%- if post.categories contains "report" -%}
    {%- unless post.index -%}
         <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endunless %}
    {%- endif -%}
{%- endfor -%}
</ul>

