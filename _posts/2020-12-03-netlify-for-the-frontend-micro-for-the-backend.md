---
layout:	post
title:	"Netlify for the frontend, Micro for the backend"
date:	2020-12-03 10:00:00
---
<br>
Today Netlify has emerged as the modern platform for rapidly building web applications without having to worry about anything beyond your code. We at [Micro](https://m3o.com)
are users of Netlify and have bought into this phenomenal experience. What's more Netlify has demonstrated to us a breakdown in the classic web architecture 
stack which previously combined web and api concerns in a single place. As we moved through a tiered architecture frontend had not been given anything more 
than hints on how to consume dynamic content from the backend. Today we're all calling this the [Jamstack](https://jamstack.org/). 

## Jamstack

<img src="https://d33wubrfki0l68.cloudfront.net/b7d16f7f3654fb8572360301e60d76df254a323e/385ec/img/svg/architecture.svg" />
<center><i><small>Credit jamstack.org</small></i></center>
<br>
The jamstack rethinks the frontend architecture by separating the concerns of static and dynamic content and pushing for the dynamic side to be consumed 
through APIs and services. Effectively, Netlify embracing this model has tried to build microservices for the frontend and moved towards a unification 
of consumption of services via APIs on the backend. It's clear this is the architecture of the future for the web and the majority of cloud services 
will be built and consumed soley as APIs.

The one question we've really been seeing a lot though is "What's Netlify for the backend?". Many of those frontend users building Jamstack apps on 
Netlify are looking to where they can find and build these APIs. It seems even Netlify's current answer has been, "go host something on heroku". I think 
in 2020 this just doesn't fly. If the frontend is being reimagined then the same has to happen on the backend to cater for that use.

## Netlify for the Backend

<img src="{{ site.baseurl }}/assets/images/netlify.png" />

[**M3O**](https://m3o.com) is a platform for cloud services development. The fastest way to build APIs without managing the infrastructure. M3O makes use of 
[**Micro**](https://micro.mu), an open source platform for microservices development. What we get from Micro is a powerful framework for building, running 
and consuming APIs as microservices. What M3O brings to the table is Micro as a Service, a fully managed platform for building microservices. Write services 
in Go and gRPC on the backend, expose them dynamically via HTTP API to be consumed by the frontend. M3O looks to fill that gap in the market for frontend 
devs. M3O is Netlify for the backend.

## M3O Features

As we mentioned, M3O is a fully managed [Micro](https://micro.mu) services platform. What does that mean? Micro provides the building blocks for 
writing, running and consuming microservices. From source to running and beyond. M3O takes that and hosts it so you can just get on with writing 
APIs without worrying about the underlying infrastructure.

Here's a few of the key features and services:

- **Microservices development** using [gRPC](https://grpc.io) and protobuf code generation
- **Service runtime** and process lifecycle management
- **Source to running** builds without need for CI/CD
- **Authentication and authorization** for access control and user management
- **Dynamic configuration** and secrets management
- **PubSub messaging** and event streaming
- **Service discovery** and secure networking
- **Key-value storage** and persistent CRUD
- **Automatic HTTP routing** with path based resolution
- **Identity aware proxy** for remote access and gRPC-web apps
- **Public API gateway** and TLS support by default
- **Public and private repos** support including  github, gitlab and bitbucket

M3O is a feature complete platform for microservices development from generating service templates on your local machine through to writing and running 
it in the cloud all using the same Micro CLI experience. M3O exposes HTTPS urls for you dynamically by default. So every service automatically becomes 
an API as soon as you deploy it.

Where a new development model has emerged for the frontend, we think its dictating the "headless" paradigm shift for the backend and M3O wants to be there 
to host all of those APIs as Micro services.

## API First

<img src="https://dev-to-uploads.s3.amazonaws.com/i/0znow24kgpu2dp3zg60n.png" />

We are seeing the emergence of APIs as the dominant form factor for cloud services, from AWS all the way through to Twilio and Stripe. What's even more 
compelling is while this model has emerged in the past few years, we are only really just getting started. It's our belief that in a decade from now 
some of the most important companies will be API first yet strangely there is no platform to caters to this form of development.

Twilio, Stripe and others have all had to build out the infrastructure for their API first approach. We think as many more companies go down this path 
the tools must emerge to empower them, not just at the compute layer but by providing the higher level abstractions required. That's the goal of M3O.

But don't just take our word for it. We're going to walk you through a demonstration of the value proposition so you can see for yourself just how 
powerful Micro and M3O are. 

## Building a backend

You're going to be writing and deploying APIs in minutes rather than hours or days! No more dealing with infrastructure on the 
backend, just as Netlify empowered devs on the frontend, we're doing the same for a new generation of developers on the backend.

Let's walk you through it. We'll deploy an existing Micro blog service with this demo frontend on Netlify: [https://loving-goodall-44ee08.netlify.app/](https://loving-goodall-44ee08.netlify.app/). But first let's start with signup.

### Signup to M3O

First you start by signing up to M3O and registering for a free account in our Dev environment.

Start by installing micro

```sh
curl -fsSL https://install.m3o.com/micro | /bin/bash
```

For those wary of curl into bash, you can view it first [https://install.m3o.com/micro](https://install.m3o.com/micro).


Signup is purely CLI based for now so just issue the following command and follow the steps

```sh
micro signup
```

Once you're done you should have an account on M3O and be automatically logged in.

### Run Helloworld

Validate that by running helloworld.

```sh
micro run github.com/micro/services/helloworld
```

Check it's running and try call it via the CLI.

```sh
# check the status
micro status

# call helloworld
micro call helloworld --name="Alice"
```

OK now we get to the more interesting part. Call it via the HTTP API that's dynamically generated for you.

```sh
# get your namespace
NAMESPACE=$(micro user namespace)

# curl your unique url
curl "https://$NAMESPACE.m3o.com/helloworld?name=Alice"
```

If alls good, we can move on to running something a bit more interesting.

### Deploying a dynamic blog backend

We're going to deploy a headless CMS, or better known as a Blog API.

On the open source side, Micro maintains some reusable example services we can all play with and contribute back to. 
You can check them out at [github.com/micro/services](https://github.com/micro/services). Let's bootstrap the blog 
using a couple of them.

Because Micro is all about microservices development, we've decomposed the blog API into posts, comments and tags. 
Right now we'll focus on posts and tags. You can find the code in [https://github.com/micro/services/tree/master/blog](https://github.com/micro/services/tree/master/blog).

Deploying these is super simple.

```sh
# run the posts service
micro run github.com/micro/services/blogs/posts

# run the tags service
micro run github.com/micro/services/blogs/tags
```

Check they're running using `micro status`. You should see the status progress through starting, building and running. 
If you want to see logs or anything related just do `micro logs posts` and the same for any other service by name.


### Write a post on the CLI

Once services are running they become immediately callable via the CLI as dynamic commands.

Save a quick post:

```sh
micro posts save --id=1 --title="My first post" --content="This is pretty epic"
```

List posts:

```sh
micro posts query
```

The same calls can be made over the API too, just have to know your namespace:

### Call it via the HTTP API

Now here's where it gets cool and more importantly what you'll be calling from your frontend apps 
running on Netlify. First grab your namespace like earlier.


```sh
$ micro user namespace
random-example-namespace
```

Now just curl it like any other api

```sh
$ curl -H "Micro-Namespace: random-example-namespace" https://api.m3o.dev/posts/query
{
  "posts": [
    {
      "id": "1",
      "title": "My first post",
      "slug": "my-first-post",
      "content": "This is pretty epic"
    }
}
```

The generic `api.m3o.dev` url requires us to pass in our namespace so we query our own service but 
every namespace also gets its own unique URL so you don't have to worry about this in your frontend 
code. Just compose namespace + m3o.dev as `random-example-namespace.m3o.dev`.

```sh
$ curl https://random-example-namespace.m3o.dev/posts/query
{
  "posts": [
    {
      "id": "1",
      "title": "My first post",
      "slug": "my-first-post",
      "content": "This is pretty epic"
    }
}
```

That's it! We now have the backend for our frontend running on M3O.

Let's deploy the sample frontend to Netlify just for kicks.

## Deploying the frontend to Netlify

The frontend is a simple angular app we've put together to validate the premise:

**Netlify for the frontend, Micro for the backend**

You can find the code in [github.com/m3o/blog-frontend](https://github.com/m3o/blog-frontend) but 
we'll walk you through the install now. The deploy settings for the site hosted under 
[loving-goodall-44ee08.netlify.app](https://loving-goodall-44ee08.netlify.app/) are as follows:

### Build settings

<center>
<img src="{{ site.baseurl }}/assets/images/deploysettings.png" style="width: 100%; height: auto;" />
</center>

<br>
You can copy the below settings for ease of use. Where you see 'concert-celtic-uncover' replace it with your namespace from `micro user namespace` on the CLI. 
We need this to know what backend API to call.

```
Repository        github.com/m3o/blog-frontend
Base directory    Not set
Build command     sed -i 's/micro/concert-celtic-uncover/g' ./src/environments/environment.prod.ts && ng build --prod && cp ./src/assets/_redirects ./dist/blog-frontend
Publish directory dist/blog-frontend
```

As you can see, it's the original `m3o/blog-frontend` being deployed in the example, but in your case `m3o` will be replaced with your fork. 
This is because Netlify asks for the permissions to the repo.

The build command is a bit involved, here is what it's doing:

```sh
# Replace the micro namespace with your own
namespace=$(micro user namespace)

sed -i "s/micro/$namespace/g" ./src/environments/environment.prod.ts

# It's an angular app, so we have to ng build
ng build --prod

# Single page applications need a redirect file
cp ./src/assets/_redirects ./dist/blog-frontend
```

After that is done and it builds successfully, your web app should be live!

Don't forget to add posts from your terminal.

### Create a new post

```sh
# Add a post
micro posts save --id=1 --title="My first post" --content="This is pretty epic"

# query posts
micro posts query
```

Now hit the frontend on Netlify and check it out. You should see your post immediately show up.

### What's the frontend doing

The frontend we're running on Netlify is basically using Micro as the backend and M3O provides the hosted 
APIs for your posts service. We're using the url `api.m3o.dev` and passing the namespace with the `Micro-Namespace` 
header but you can equally use unique API urls that are `$namespace.m3o.dev`.

Each service you deploy resolves to a path e.g the 'posts' service is api.m3o.dev/posts and their methods follow on from that so 
`Posts.Query` on the backend is `api.m3o.dev/posts/query`. This provides automatic dynamic mapping of Go based gRPC 
services on the backend to HTTP APIs for the frontend.

Here's the example code in typescript we use to construct the calls

```
export class M3oService {
  public address: string = environment.m3oAddress;
  public namespace: string = environment.m3oNamespace;

  constructor(private http: HttpClient) { }

  get(service: string, endpoint: string, params: HttpParams): Promise<Object> {
    return this.http.get(this.address + "/" + service + "/" + endpoint, {
      headers: {
        "Micro-Namespace": [this.namespace]
      },
      params: params,
    }).toPromise()
  }
}
```

And here's us listing those posts on the frontend

```
  ngOnInit(): void {
    this.m3o.get("posts", "query", null).then(v => {
      this.posts = v["posts"]
    })
  }
```

## Micro is Netlify for the backend

It's really clear to us that there's this huge pain for people trying to consume APIs as we move into this new rearchitected world. 
Too often people are asking "Where do I write or host my APIs", they are asking **Where's the Netlify for the backend**. We think 
M3O and Micro are that solution. 

It's not enough to just consume existing APIs in the ecosystem, you want to build your own, but 
you want to do it without having to standup layers of infrastructure on AWS or be beholden to the legacy players like Heroku or 
other providers who don't get that you want the same Netlify like experience on the backend.

Hopefully you're feeling like this makes sense and if you do please try out [M3O](https://m3o.com) and come join the [Slack](https://slack.m3o.com) 
to chat with us. Write, run and consume all free, for personal use, with friends or your team. Hack on side projects, build APIs 
to scale and either use it as the backend for your frontend or build the next Twilio or Stripe, all on M3O with Micro.
