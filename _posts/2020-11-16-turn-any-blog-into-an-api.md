---
layout:	post
title:	"Turn any blog into an API"
date:	2020-11-16 10:00:00
---
<br>
Last time we talked to you about how we believe Micro is [Netlify for the backend]({{ site.baseurl }}/2020/11/12/netlify-for-the-frontend-micro-for-the-backend.html). 
We got a very strong positive reaction to that, filling a pain point it looks like many people had. In that post we used headless cms aka blog posts 
as an example of the API you'd build on the backend to be consumed by a frontend. Today we're going to take it a step further.

An API on its own isn't enough. There's no content. You have to populate it yourself. So what if we made it just a little bit easier. How about we help
 you turn any blog, any content with an rss feed into an easy to consume API with just a handful of commands. Exciting right, let's get to it.

## Deploying the blog backend

Firstly, if you weren't around for the other post, we'll help you deploy the existing posts api. Firstly you'll need to signup.

### Signup

Start by installing micro if you haven't already

```sh
curl -fsSL https://install.m3o.com/micro | /bin/bash
```

For those wary of curl into bash, you can view it first [https://install.m3o.com/micro](https://install.m3o.com/micro).


Signup is purely CLI based for now so just issue the following command and follow the steps

```sh
micro signup
```

Once you're done you should have an account on M3O and be automatically logged in.

### Run Services

All the services you're going to run are open source. You can check them out at [github.com/micro/services](https://github.com/micro/services). 
Let's bootstrap the blog super quick. Because Micro is all about microservices development, we've decomposed the blog API into posts, comments and tags. 
You can find the code in [https://github.com/micro/services/tree/master/blog](https://github.com/micro/services/tree/master/blog).

Deploying these is super simple.

```sh
# run the posts service
micro run github.com/micro/services/blog/posts

# run the tags service
micro run github.com/micro/services/blog/tags

# run the comments service
micro run github.com/micro/services/blog/comments
```

Check they're running using `micro status`. You should see the status progress through starting, building and running. 
If you want to see logs or anything related just do `micro logs posts` and the same for any other service by name.


