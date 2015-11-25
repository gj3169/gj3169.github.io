---
layout: page
title: 
tagline: I think, therefore I am.
---
{% include JB/setup %}

##强烈推荐

**[简便易行VPN搭建方法](http://simongong.net/2015/09/%E6%90%AD%E5%BB%BAvpn%EF%BC%8C%E4%BD%8E%E4%BB%B7%E4%BA%AB%E7%94%A8%E8%87%AA%E5%B7%B1%E7%8B%AC%E4%BA%AB%E7%9A%84vpn/)**

## 文章列表



{% if paginator.page > 2 %} 
<li><a href="/page{{paginator.previous_page}}/">上一页</a></li> 
{% endif %} 
{% assign pageSize = 5 %} 
{% assign startPage = paginator.page | minus:pageSize %} 
{% if 2 > startPage %}	
{%	assign startPage = 2 %} 
{% endif %} 
{% assign endPage = paginator.page | plus:pageSize %} 
{% if endPage >= paginator.total_pages %}	
{%	assign endPage = paginator.total_pages | minus:1 %} 
{% endif %} 
{% for count in (startPage..endPage) %} 
{% if count == paginator.page %} 
<li><a href="#"><span class="current-page">{{count}}</span></a></li> 
{% else %} 
<li><a href="/page{{count}}/">{{count}}</a></li> 
{% endif %} 
{% endfor %} 
{% if paginator.next_page %} 
<li><a href="/page{{paginator.next_page}}/">下一页</a></li> 
{% endif %} 
<li><a href="/page{{paginator.total_pages}}/">末页</a></li> 
<li><a href="#">第{{paginator.page}}页 / 共{{paginator.total_pages}}页</a></li>
