---
title: about
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
  <h3>{% t about.contact %}</h3><a class ="Contact" id="Contact"></a>
  {% t about.contact_message %}
  <form id="second" method="post" action="https://briskforms.com/go/6326a6cc0d3a86c7aaf91d2fa55606b0">
        <input type="text" placeholder="{% t about.name %}" name="name" >
        <input type="email" placeholder="{% t about.email %}" name="_replyto" required >
        <textarea form ="second" name="message" rows = "3" cols = "80" placeholder="{% t about.message %}"></textarea>
        <input type="checkbox" name="Subscribe" value="Add me"> "{{ t about.subscribe }}"
        <label for="Subscribe">
        </label>
        <input type="submit" value="{% t about.send %}">
    </form>

</html>
