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
  <h3>{% t about.contact %}</h3><a class ="Contact" id="Contact"></a>
  {% t about.contact_message %}
  <form id="second" method="post" action="https://forms.un-static.com/forms/f589de0bf21a5148ee4cae28f412f326f36288ef">
        <div class="wrapper">
          <input class="inputbold" type="text" name="" placeholder="boldinput" />
          <input class="inputbold" type="text" name="" placeholder="blah" />
        </div>
        <input type="text" placeholder="{% t about.name %}" name="name" />
        <input type="text" placeholder="Personal URL" name="link" >
        <input type="email" placeholder="{% t about.Email %}" name="_replyto" required >
        <textarea form ="second" name="message" rows = "3" cols = "80" placeholder="{% t about.message %}"></textarea>
        <input type="checkbox" name="Subscribe" value="Add me"> {% t about.Subscribe %}
        <label for="Subscribe">
        </label>
        <input type="submit" value="{% t about.send %}">
    </form>

</html>
