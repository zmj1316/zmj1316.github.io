---
layout: page
title: 分类
---

<style>
		h1 { position: fixed; width: 100%; text-align: center; background: red; color: white; padding: 180px 0 30px; top: 0; left: 0; z-index: 1000; }
		h1 span { display: block; font-size: 75%; }
		h2, ul {  }
		h3, span, #top { margin-top: -300px; padding-bottom: 300px; display: block; }
</style>

<div class="tag_posts">
{% for tag in site.categories %} 
	<a name="{{ tag[0] }}"></a>
    <h3   id = "{{ tag[0] }}" >{{ tag[0] }}({{ tag[1].size }})</h3>
	<ul>
	{% for post in tag[1] %}
		<li><span>{{ post.date | date:"%Y-%m-%d" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
	</ul>
{% endfor %}
</div>
