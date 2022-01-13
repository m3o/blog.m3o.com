---
layout: post
title:  "Launching M3O Carbon"
date:   2022-01-13 10:00:00
---
<br>
Today we're announcing [M3O Carbon](https://m3o.com/carbon), a way to purchase carbon offsets programmatically.

To get started just head to [M3O](https://m3o.com), signup and check out the [Carbon](https://m3o.com/carbon) service.

## Carbon API

Climate change is an important issue and one that the world has finally started to focus on. We all have a responsibility 
to help offset our carbon emissions and part of that as a company is not only to contribute to it directly but to also 
enable others to do the same.

Here's a quick rundown of how to use it


### Purchase Carbon Offsets

You can currently purchase 1KG (or 0.001 tonnes) of carbon offsets in a single request.

```
curl "https://api.m3o.com/v1/carbon/Offset" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $M3O_API_TOKEN" \
    -d '{}'
```

And the response should look something like this

```
{
    "units": 1,
    "metric": "KG",
    "tonnes": 0.001,
    "projects": [
        {
            "name": "Producing electricity from wind power in Northeast Thailand",
            "percentage": 98,
            "tonnes": 0.00098
        },
        {
            "name": "Wind power generation in Bac Lieu Province, Vietnam",
            "percentage": 2,
            "tonnes": 0.0002
        }
    ]
}
```

Call the API as many times as you need to purchase the amount of offsets required. The endpoint is currently 
priced at $0.01 per request.


And that's it. Signup for free at [m3o.com/register](https://m3o.com/register) or join the community on [Discord](https://discord.gg/TBR9bRjd6Z0) to learn more.

Thanks for reading!
