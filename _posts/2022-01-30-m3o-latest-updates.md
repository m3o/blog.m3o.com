---
layout: post
title:  "M3O Latest Updates"
date:   2022-01-30 10:00:00
---
<br>
A belated happy new year to you all.  We hope you enjoyed the holiday period, got the chance to chillout and perhaps even hack on some random side projects if that's your kind of thing during the off time.

We kick off the new year with a bang! [M3O](https://m3o.com) launched back in July 2021, since then we've had thousands of developers signup, served hundreds of thousands of API requests each month and put 50 of the most vital building blocks on the platform.

Today we'll share a few of those APIs with you, and guess what, they're entirely FREE to start.

[M3O Apps](https://m3o.com/app) - One of the most painful things about the cloud is launching and managing apps, especially programmatically. It's either too expensive or too complicated. So we simplified it and made it free. Launch apps with one API call or CLI command from source. Get 10 apps for free. It's just that simple.

[M3O DB](https://m3o.com/db) - Simple database service. The most popular API on our platform, provides basic CRUD on top of managed postgres. While everyone loves SQL, it's clear the world is shifting to be serverless, API first and with that we think the M3O DB serves at the core of that with a simple JSON based CRUD API.

[M3O Users](https://m3o.com/user) - User management and authentication. Stop rebuilding signup and login for every new app you write. The M3O Users service should be the last API you ever need for this, including verification and password reset emails.

[M3O Events](https://m3o.com/event) - Send and receive real time events. PubSub, queuing, streaming, notifications. Whatever you want to call it. We need it, async messaging is so core to app building. But what are we supposed to use? Kafka? Google PubSub? It's gotta be easier than that right? Yup, with the M3O Events API it is.

[M3O Space](https://m3o.com/space) - Infinite cloud storage. We've all come to see S3 as the defacto cloud storage service, yet for all it's worth, we think the API needs to be much simpler, so we built a better API. M3O Space offers long term object storage built on top of existing S3 providers.

[M3O Search](https://m3o.com/search) - Indexing and full text search. We know every great app has search. So why is it so hard to find a decent search API? Running elasticsearch is either really painful or costs a lot of money. We built the search API to make it dead simple and easy to get started without all the fuss.
 
## New Features

In other news, we're hard at work building out a couple of cool new features for the platform driven by user demand. The first is a cloud dashboard that will enable you to manage your apps, data and more through an easy to use UI rather than API calls. You can try out the alpha at [https://cloud.m3o.com](https://cloud.m3o.com).

The second feature we're working on is subscriptions with tiers; Free, Pro and Team. A lot of people have mentioned the pay-as-you go top-up model is nice but impractical for production use. We've heard you and soon you'll be able to use recurring payments with additional features, support and quota. 
 
## New Landing Page

We also got a shiny new landing page!

<p style="text-align: center;">
  <a href="https://m3o.com"><img src="{{ site.baseurl}}/assets/images/m3o-landing-page.png" style="width: 100%; margin: 0 auto;" /></a>
</p>

## Community Driven Development

We're using a community first approach to build M3O. This is the first cloud provider where you get to actively engage in the roadmap, provide feedback directly to the team and be part of a growing community all building the next generation cloud together.

[Join us on Discord](https://m3o.chat)
 
## Open Source by Default

We've spent years as creators of open source, first with the [Go Micro](https://go-micro.dev) framework and then with the [Micro](https://micro.dev) platform. Today, there is no cloud provider that's truly open source by default. While they might host open source projects, the majority of their platform is closed source.

So for that reason, we open sourced M3O, learn more at [https://m3o.dev](https://m3o.dev).
 
## Thanks for reading!

We hope you enjoyed the latest update. Come join us on [Discord](https://m3o.chat) if you have any questions, signup at [https://m3o.com](https://m3o.com) and let us know if you have any feedback or requests for APIs.
