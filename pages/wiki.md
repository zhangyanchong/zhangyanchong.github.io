---
layout: page
title: Wiki
description: 人越学越觉得自己无知
keywords: 刘方亭的维基, Wiki
comments: false
menu: 维基
permalink: /wiki/
---

> 好记性不如烂笔头。不积跬步，无以至千里；不积小流，无以成江海。

<ul class="listing">
{% for wiki in site.wiki %}
{% if wiki.title != "Wiki Template" %}
<li class="listing-item"><a href="{{ site.url }}{{ wiki.url }}">{{ wiki.title }}</a></li>
{% endif %}
{% endfor %}
</ul>
