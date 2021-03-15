---
layout: post
title:  "How we built Distributed with Next.js and Micro"
date:   2021-03-30 10:00:00
---
<br>
[Distributed](https://joindistributed.com) is a live social chat app built as a Jamstack demo using [Next.js](https://nextjs.org/)
and [Micro](https:/micro.mu). We built it to demonstrate the value proposition of [M3O](https://m3o.com) - a cloud platform for API development. 
This post explains what went into building Distributed in just a few weeks and how M3O helped rapidly build our MVP.

## Jamstack Development

Jamstack is a new architecture pattern for frontend which offloads dynamic aspects of the stack to javascript and third party APIs. 
[Vercel](https://vercel.com/), the makers of [Next.js](https://nextjs.org/) and related companies are pioneering the way forward 
for jamstack development.

<img src="https://d33wubrfki0l68.cloudfront.net/b7d16f7f3654fb8572360301e60d76df254a323e/385ec/img/svg/architecture.svg" />
<center><i><small>Credit jamstack.org</small></i></center>
<br>

JAMstack stands for Javascript, API and Markup. The static part of the application is deployed to a CDN with javascript 
dynamically loading various pieces of dynamic content from backend APIs and rendering it.

## Why we chose Next.js

Next.js is a massively popular react based framework for Jamstack development. When we were looking at building out a demo on top of [M3O](https://m3o.com) 
we had the choice of going down a number of routes but what really appealed to us was the how deliberate a lot of the choices were in how the Vercel 
team had constructed the Next.js framework.

Being framework creators ourselves with the dominant framework [Go Micro](https://github.com/asim/go-micro) for Go, we could appreciate the efforts 
required and strong opinions needed to drive such adoption and success. Vercel has done a phenomenal job in this way.

## Server Side Rendering

## Building on Netlify

## Switching to Self Hosted

One of the major issues we faced during our 

<INSERT IMAGE OF CROSS ATLANTIC HOPPING>

## Performance

## Conclusions

