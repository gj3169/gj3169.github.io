---
layout: page
title: 
tagline: I think, therefore I am.
---
{% include JB/setup %}

##强烈推荐
[简便易行VPN搭建方法](http://simongong.net/2015/09/%E6%90%AD%E5%BB%BAvpn%EF%BC%8C%E4%BD%8E%E4%BB%B7%E4%BA%AB%E7%94%A8%E8%87%AA%E5%B7%B1%E7%8B%AC%E4%BA%AB%E7%9A%84vpn/)
## 文章列表

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>




