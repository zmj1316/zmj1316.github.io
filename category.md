---
layout: page
title: 分类
---
<script type="text/javascript">
	window.onload = function(){
		if (window.location.hash.indexOf('#') >= 0) {
			$('html,body').animate({
				scrollTop: ($(window.location.hash).offset().top - 150) + "px"
			},
			300);
		}; //主要修复评论定位不准确BUG
	}
</script> 



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
