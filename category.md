---
layout: page
title: 分类
---
<!-- <svg class="cloud" style="width:95%;height:600px">
    <g></g>
</svg> -->
<div class="tag_posts">
{% for tag in site.categories %} 
	<a name="{{ tag[0] }}"></a>
    <h3 id = "{{ tag[0] }}">{{ tag[0] }}({{ tag[1].size }})</h3>
	<ul>
	{% for post in tag[1] %}
		<li><span>{{ post.date | date:"%Y-%m-%d" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
	</ul>
{% endfor %}
</div>
