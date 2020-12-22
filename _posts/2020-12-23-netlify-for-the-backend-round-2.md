---
layout:	post
title:	"Netlify for the Backend - Round 2: Reusable Micro Services"
date:	2020-12-23 10:00:00
---
<br>
Last month we talked about a new architecture pattern, <a href="{{ site.baseurl }}/2020/11/12/netlify-for-the-frontend-micro-for-the-backend.html">Netlify for the frontend, Micro for the backend</a>. As the frontend has evolved towards being dominated by the <a href="https://jamstack.org/">Jamstack</a>, we believe the backend also requires a fundamental shift in it's design and consumption model. 

Netlify, while largely agnostic of framework usage, has promoted decomposition of the traditional stack to something more driven by microservices and APIs. 
[Micro](https://m3o.com) has long been an advocate for that, both as an [open source](https://github.com/micro/micro) project and now has a hosted platform called 
[M3O]({{ site.baseurl }}/2020/11/05/m3o-open-to-the-world.html).

## Evolution of the Backend

But what's more, we're seeing a need from the backend to evolve beyond providing traditional infrastructure services. It's no longer enough to just provide 
authentication, configuration, storage, hosting, etc. What we really need is higher level APIs that provide business level value. 

The most prime examples are Stripe, Twilio, Sengrid and Segment. Who focus on APIs for finance, communications and analytics. AWS, Google and others are providing 
coverage for infra level APIs.

What we really need is the next layer of abstraction. We need the building blocks for new types of APIs and services.

<center>
  <img src="{{ site.baseurl }}/assets/images/building-blocks.png" style="width: 100%; height; auto;" />
</center>

