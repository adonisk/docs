---
layout: default
title: FAQ
description: related to Ezetap integration
type: Help
---

<ol>
  {% for post in site.posts %}
    <li>
		<a href="javascript:togglePost('p_{{ post.id }}');"<b>{{ post.title }}</b></a>
		<div id ="p_{{ post.id }}" style="display:none" class="post-content">
			{{ post.content }}
		</div>
    </li>
  {% endfor %}
</ol>

<script language="javascript"> 
function togglePost( p_id ) {
	var ele = document.getElementById(p_id);
	if(ele.style.display == "block") { ele.style.display = "none"; }
	else { ele.style.display = "block"; }
} 
</script>
 
<a id="displayText" href="javascript:toggle();">show</a> <== click Here
<div id="toggleText" style="display: none"><h1>peek-a-boo</h1></div>