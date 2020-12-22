---
layout:	post
title:	"The backend for your jamstack"
date:	2020-12-23 10:00:00
---
<br>
Last month we talked about a new architecture pattern, <a href="{{ site.baseurl }}/2020/11/12/netlify-for-the-frontend-micro-for-the-backend.html">Netlify for the frontend, Micro for the backend</a>. As the frontend has evolved towards being dominated by the <a href="https://jamstack.org/">Jamstack</a>, we believe the backend also requires a fundamental shift in it's design and consumption model. 

Netlify, while largely agnostic of framework usage, has promoted decomposition of the traditional stack to something more driven by microservices and APIs. 
[Micro](https://m3o.com) has long been an advocate for that, both as an [open source](https://github.com/micro/micro) project and now as a hosted platform called 
[M3O]({{ site.baseurl }}/2020/11/05/m3o-open-to-the-world.html).

## Get Started

If you want to skip right to getting started head to the [m3o.com/signup](https://m3o.com/signup). 

## Evolution of the Backend

But what's more, we're seeing a need from the backend to evolve beyond providing traditional infrastructure services. It's no longer enough to just focus on
authentication, configuration, storage, hosting, etc. What we really need is higher level APIs that provide business level value. 

The most prime examples are Stripe, Twilio, Sengrid and Segment. Who focus on APIs for finance, communications and analytics. AWS, Google and others are providing 
coverage for infra level APIs.

What we really need is the next layer of abstraction. We need the building blocks for new types of APIs and services. Micro acts as a platform for these 
services and now we want to move into offering the next level of value add services.

## Composition and Value Add

What's clear when working with microservices is that there's an ability to decompose systems into smaller domain specific reusable services and then aggregate back 
up into many forms as value add services, products and then businesses.

<center>
  <img src="{{ site.baseurl }}/assets/images/building-blocks.png" style="width: 100%; height; auto;" />
</center>

As you can see in this image and probably from common experience, most businesses are composed of the same generic building blocks from the infrastructure all the 
way up. It's only when we get to the business specific requirements that we need our own services to handle that logic.

It's insane that most of us continue to build the same systems on the backend over and over rather than reusing and building on the foundations of each others 
work. GitHub enabled this for open source at an accelerated pace but we've yet to see the same emerge for business logic, services and APIs.

It's now our goal to facilitate this with a single unified platform and reusable services.

## Introducing Micro Services

Today we're unveiling [**Micro Services**](https://github.com/micro/services), a set of reusable building block services which can be used on the Micro Platform 
whether you're self hosting the [open source](https://github.com/micro/micro) project or using our managed platform [M3O](https://m3o.com).

Browse directly to [github.com/micro/services](https://github.com/micro/services) if you want to read through the code or kick the tyres locally.

<center>
  <img src="{{ site.baseurl }}/assets/images/micro-services.png" style="width: 100%; height: auto;" />
</center>

<br>

### What's Included?

We're including 10 services from the get go.

- Helloworld
- Chat
- Posts
- Comments
- Tags
- Feeds
- Location
- Messages
- Notes
- Users

All of the above services are available to explore and deploy when logged in on [web.m3o.com](https://web.m3o.com/).
<center>
  <img src="{{ site.baseurl }}/assets/images/new-service.png" style="width: 90%; height; auto;" />
</center>

After selecting and running a service, an instance of it gets deployed to your namespace. Once the service deploys it's API endpoints can be explored and 
called directly from the web UI along with its running status and logs.

<center>
  <img src="{{ site.baseurl }}/assets/images/callendpoint.png" style="width: 90%; height; auto;" />
</center>
<br>
All the services running can be called from Javascript easily (currently only a vanilla JS client is available, more is coming), see the embed tab for the code.

<center>
  <img src="{{ site.baseurl }}/assets/images/microjs.png" style="width: 90%; height; auto;" />
</center>
<br>

Micro.js handles authentication (a popup appears with a login or register options), so even endpoints requiring authentication or authorization can be called.
Micro.js, combined with a lighweight templating language can be a perfect tool to add dynamic functionality to static pages by running the backend on Micro and calling those services with Micro.js.

For those interested in a typescript implementation of login, signup, user read and token refreshing API calls, the [relevant web dashboard code](https://github.com/micro/web/blob/main/src/app/user.service.ts) can be useful.