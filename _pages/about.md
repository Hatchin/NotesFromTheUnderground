---
title: 
  en: About Here
  zh: 关于此地
layout: single
permalink: /about/
author_profile: true
header:
  overlay_image: /assets/images/teaser.JPG
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background

---

<p>{% t about.intro %}</p>

<html>
<br>
  <h2 class="archive__subtitle">{% t about.contact %}</h2>
  <h3>{% t about.contact_message %}</h3>
  <form id="second" method="post" action="https://getsimpleform.com/messages?form_api_token=bce488d72133f1c308485c01fad8b4bb" >
        <input name="redirect_to" type="hidden" id="name" value="https://hatchin.netlify.com{{site.baseurl}}/thankyou">
        <input type="text" placeholder="{% t about.name %}" name="name" required>
        <input type="text" placeholder="{% t about.personal_url %}" name="link" >
        <input type="email" placeholder="{% t about.Email %}" name="replyto_" required >
        <textarea form ="second" name="message" rows = "3" cols = "80" placeholder="{% t about.message %}"></textarea>
        <input type="checkbox" name="Subscribe" value="Add me"> {% t about.Subscribe %}<label for="Subscribe"></label>
        <input type="checkbox" name="Private" value="Add me"> {% t about.private %}
        <label for="Private">
        </label>
        <input type="submit" value="{% t about.send %}">
    </form>
<br>
<br>
<div class="page__innerwrap"><h2>脚印</h2>
	<div class="comment" id="comment-1">
		<b><font size="4em"><a href="http://www.mryu.top/" target="_blank">spain</a> Say:</font></b>
			<p class="aboutcomment"><font size="3.5em"> github 搜 Crawler4Caida 来的，<br>
								    有个资源不能爬了 哈哈<br>
								    请指教</font><br>
				<font size="3em">2019-12-20 10:05</font><a href="{{ "/about/#Contact" | prepend: site.baseurl  }}">回复</a>
		</p>	
		<b><a href="http://www.mryu.top/" target="_blank">云中布衣</a> </b><br><span class="comment-time">2019-12-21 09:35</span>
				<div class="comment-content">@xiaopan：哪个？</div>
				<div class="comment-reply"><a href="http://www.mryu.top/about.html#comment-396" onclick="commentReply(396,this)">回复</a></div>		

		</div>
		<hr style="height:1px;border:none;border-top:1px dashed grey;">
	</div>

</html>
