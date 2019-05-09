---
title: "About Me"
layout: single
permalink: /about/
author_profile: true
subscribe : true
header:
  overlay_image: /assets/images/teaser.JPG
  overlay_filter: 0.3 # same as adding an opacity of 0.5 to a black background

---

Oh hey — 

This is Hatchin, just an ordinary person, a wandering machine learning practitioner, a fan of Dostoevsky, and usually a homebody who enjoy travelling. 

I work as a Data Scientist focused on Deep Learning and predictive analytics. Up to now I am based in Bay Area. Here is my blog for everything about Data Science I would like to share. 

{% if page.subscribe %}
    <h4>Subscribe</h4>
    <form action="https://formspree.io/sangyushen@gmail.com"
        method="POST">
        <input type="text" placeholder="Name" name="name" style="height:36px; width:150px">
        <input type="email" placeholder="Email" name="_replyto" required style="height:36px; width:150px">
        <input type="message" placeholder="Message(if any)" name="message" style="height:36px; width:150px">
        <input type="submit" value="Get Updates" style="height:36px; width:150px">
    </form>
  {% endif %}
