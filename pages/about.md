---
layout: page
title: About 张三
description: 程序人生
keywords: 张艳冲, zhangsan, php_zhangyanchong, zhangyanchong ,张艳冲的个人博客
comments: true
menu: 关于
permalink: /about/
---

大家好，我是张三，目前在研究微服务、Docker、K8s、分享开源技术。

坚信熟能生巧，坚持不懈，技术改变人生。

业余台球、快走、乒乓球，电影，电视好者。

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
