---
layout:	post
title:	"Embed a Wordpress blog anywhere on the web"
date:	2020-11-25 10:00:00
---
<br>
Last time we spoke to you about [Turning any blog or RSS feed into an API]({{ site.baseurl }}/2020/11/16/turn-any-blog-or-rss-feed-into-an-api.html) using Micro 
and services hosted on M3O. Today we're going to continue that story and show you how to embed a wordpress blog anywhere on the web for free.

Wordpress is a massive blogging platform, powering over 35% of content on the internet in 2020. The stats are staggering. Over 400 million people 
visit wordpress sites each month and yet getting this content back out in a reusable, programmable and easily digestable form today is really tough.

<i>See more on the stats at [https://hostingtribunal.com/blog/wordpress-statistics/](https://hostingtribunal.com/blog/wordpress-statistics/)</i>

## Why wordpress matters?

Why does it matter? How is it relevant to M3O? We want to unlock backend API development for frontend developers everywhere. Part of that story 
is showing you how powerful the M3O platform can be and leveraging it for relevant services today. 

Right now headless CMS is all the rage but that really focuses on content creation on the same platform. While we can enable it and have show 
cased building a blog as an API we think content creation already happens in places with great tooling like Wordpress. The hard part is getting 
that content out in a form we can consume e.g an API.

Wordpress is where a huge majority of content is siloed. We can extract that as RSS, maybe even find some painful php code to turn it into 
widgets but the reality is, we need a better way. Wordpress blogs need an API and that needs a faster and simpler way to be embedded everywhere.

## API-ify the blog

So how do we go about doing? Well if you check out the [previous]({{ site.baseurl }}/2020/11/16/turn-any-blog-or-rss-feed-into-an-api.html) blog post you'll see 
that we can take any RSS feed, crawl it and resurface as a simple HTTP API. If you want to checkout the code for that head to 
[github.com/micro/services/blog](https://github.com/micro/services/tree/master/blog). Completely open source and free for anyone to use. If you just 
want to deploy it and kick the tyres, check out the previous post.

OK so wordpress has made it really easy to [find your RSS feed](https://wordpress.org/support/article/wordpress-feeds/#finding-your-feed-url). 

You can either use the following

```
http://example.com/?feed=rss
http://example.com/?feed=rss2
http://example.com/?feed=rdf
http://example.com/?feed=atom
```

Or for custom permalinks

```
http://example.com/feed/
http://example.com/feed/rss/
http://example.com/feed/rss2/
http://example.com/feed/rdf/
http://example.com/feed/atom/
```

In our case we just want the standard RSS feed.
