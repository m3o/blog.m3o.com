---
layout: post
title:  "Launching M3O Space"
date:   2021-12-23 10:00:00
---
<br>
Today we're announcing [M3O Space](https://m3o.com/space) aka infinite cloud storage.

To get started just head to [M3O](https://m3o.com), signup and check out the [Space](https://m3o.com/space) service.

## Space API

The space API is effectively what we think of as CRUD for infinite cloud storage. It's backed by S3 and provides 
one place to put all your images, files, videos, etc. But why not just use S3 directly? Personally we found 
the S3 api at this point to be pretty cumbersome. It's a building block for infrastructure but maybe not how we 
should directly interact with a storage API today.

### Create an Object

Here's how you'd create an object in space:

```
curl "https://api.m3o.com/v1/space/Create" \
    -H "Authorization: Bearer $M3O_API_TOKEN" \
    -Fobject=@file.jpg -Fname=images/file.jpg -Fvisibility=public
```

A url will then be returned like so:

```
https://space.m3ocontent.com/micro/3db66283-55b5-4e6e-9c83-de9e53959db0/images/file.jpg
```

## Read the Object

To read small files directly though the API

```
curl "https://api.m3o.com/v1/space/Read" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $M3O_API_TOKEN" \
    -d '{
      "name": "images/file.jpg"
    }'
```

## Private Objects

To create private objects just specify `visibility=private` at time of creation, then download it directly through the API.

```
curl -L "https://api.m3o.com/v1/space/Download" \
-H "Content-Type: application/json" \
-H "Authorization: Bearer $M3O_API_TOKEN" \
-d '{
  "name": "images/file.jpg"
}'
```

And that's it. Signup for free at [m3o.com/register](https://m3o.com/register) or join the community on [Discord](https://discord.gg/TBR9bRjd6Z0) to learn more.

Thanks for reading!
