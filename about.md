---
layout: page
permalink: /about/index.html
title: Kapil Kumar
tags: [kapil,kumar, kapilkd13]
imagefeature: fourseasons.jpg
chart: true
---

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}


My name is Kapil Kumar. I am a third year Undergraduate student of Computer Science at National Institute of Technology, Delhi. I spent my childhood in Jaipur( A beautiful city and this is where I belong to :)) and from past 8 years I have been living in Delhi.  
To be honest, I never thought of being a Software Engineer in my childhood, but with time I came across magical( they were magical for me at that age) things my cousin could do with few click on computer.  
I always wanted to leave an impact on the world and soon I realized writing programs that do amazing things is the fastest way to do so.
