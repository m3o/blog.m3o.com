---
layout: post
title:  "Launching M3O Apps"
date:   2021-12-23 10:00:00
---
<br>
Today we're announcing [M3O Apps](https://m3o.com/app). A quick way to deploy any app for free.

To get started just head to [M3O](https://m3o.com), signup and check out the [Apps](https://m3o.com/app) service.

## Apps API

Apps are central to all that we do. It's the main way we've come to consume services, and there's no limit to the number 
of App deployment platforms we have. DigitalOcean, Heroku, AWS, Render, the list goes on and on. Yet for us it still 
felt like app deployment was really something falling short, either being super opinionated and entirely restricted 
or incredibly complex and difficult to use from an API.

We'd always imagined the ability to simply curl an endpoint to deploy an App but it's never that simple. Today though 
we're making it happen. You can now programmatically deploy an app with one API call.

### Helloworld

Here's a helloworld example:

```
curl "https://api.m3o.com/v1/app/Run" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $M3O_API_TOKEN" \
    -d '{
       "name": "helloworld",
       "repo": "github.com/asim/helloworld"
    }'
```
### Custom URLs

What's more, on most platforms the URLs are often something really messy unless you provide a custom domain. We wanted
something simple by default. Each app gets a custom `*.m3o.app` domain which you can either reserve or get something 
pregenerated much like usernames on social platforms.

Helloworld lives at [helloworld.m3o.app](https://helloworld.m3o.app).

### Reserve URLs


You can reserve app URLs like so:

```
curl "https://api.m3o.com/v1/app/Reserve" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $M3O_API_TOKEN" \
    -d '{
        "name": "helloworld"
    }'
```

And that's it. Signup for free at [m3o.com/register](https://m3o.com/register) or join the community on [Discord](https://discord.gg/TBR9bRjd6Z0) to learn more.

Thanks for reading!
