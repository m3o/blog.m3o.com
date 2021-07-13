---
layout: post
title:  "Micro APIs - Programmable building blocks for everyday use"
date:   2021-06-24 10:00:00
---
<br>
Today we’re excited to announce our new [Micro API](https://m3o.com) cloud platform, now in beta. Simple, fast and affordable APIs for everyday use. 
[Signup for free](https://m3o.com) (no credit card needed) and get $5 of free credit to get started.

<center>
<img src="{{ site.url }}/assets/images/landing-page.png" style="width: 100%; border: 1px solid #ccc;"/>
</center>
<br>
## API building blocks

Micro has evolved from an open source framework to a full blown API platform, one that continues to focus on the developer experience first and foremost. The majority of our users are building APIs for end public consumption but having to rebuild many of the building blocks they need wherever they go.

We wanted to solve that problem by providing a set of programmable building block services as simple APIs for public consumption from anywhere in the world, all in one place.

Some of the APIs we’re offering are as follows:

- [Cache - Ephemeral key-value storage](https://m3o.com/cache) - 
Store any data up to 1mb for fast key based lookup. Set TTLs to expire entries so you don’t have to remember to delete them.

- [DB - Simple database service](https://m3o.com/db) - 
Use CRUD via an API and leave the SQL behind. A really dead simple database service which provides JSON document storage.

- [Crypto - Cryptocurrency prices and quotes](https://m3o.com/crypto) - 
Stay up to date with bitcoin, ethereum, dogecoin and other prices. Track them in real time and build any sort of visualisation on top.

- [Image - Upload, resize and crop images](https://m3o.com/image) - 
Upload images, resize on the fly and serve them via a CDN all without having to do anything more than curling our API.

- [OTP - One time password generation](https://m3o.com/otp) - 
Throwaway the passwords and use one time token generation to login or authenticate users. Simple OTP generation and validation.

- [Routing - Turn by turn directions and etas](https://m3o.com/routing) - 
A vastly cheaper Google Maps API alternative powered by OSRM. We’ll give you turn by turn routing directions and etas using OpenStreetMap data.

## Third Party APIs

Additionally we’ve partnered with third party API providers such as [Finage](https://finage.co.uk/), [ExchangeRate-API](https://www.exchangerate-api.com/) and the 
[WeatherAPI](https://www.weatherapi.com/) to bring more functionality to the platform like [Currency](https://m3o.com/currency) conversion, [Stock](https://m3o.com/stock) 
prices and [Weather](https://m3o.com/weather) forecasts, so you can access everything you need with just one account and one API key, all in one place. We’re adding 
more and more third party API providers everyday so keep your eyes peeled!

## Taming Complexity

AWS is the cloud giant in the sky we've all come to know as the definition of API building blocks but over time it's complexity has also grown, making it 
more and more difficult to work with as a developer. We see this, we feel this and we know there needs to be a change.

Micro attempts to remove the marketing spiel, cloud complexity and bottomless billing by doing the following:

- API docs and usage are always just one click away
- Billing is Top-Up only. Only use the credit in your account
- Everything can be accessed via Curl or any simple HTTP library

Here's some of what we're talking about.

API docs provide examples and usage along with the pricing clearly next to the endpoint

<center>
<img src="{{ site.url }}/assets/images/api-doc.png" style="width: 100%; border: 1px solid #ccc;"/>
</center>
<br>

Test out the API right there in the UI

<center>
<img src="{{ site.url }}/assets/images/query-page.png" style="width: 100%; border: 1px solid #ccc;"/>
</center>
<br>

We'll add $5 free credit to your account to start but just top-up with however much you need

<center>
<img src="{{ site.url }}/assets/images/billing-page.png" style="width: 100%; border: 1px solid #ccc;"/>
</center>
<br>

Then just head to the token page to create yourself a well scoped token for external use

<center>
<img src="{{ site.url }}/assets/images/token-page.png" style="width: 100%; border: 1px solid #ccc;"/>
</center>
<br>

And finally. Curl it from anywhere!

```
curl "https://api.m3o.com/v1/id/Generate" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $MICRO_API_TOKEN" \
  -d '{"type": "snowflake"}'
```

## Thanks for reading

Hopefully you buy into what we're talking about and the need for something new in the API space.
If you like what you’re hearing, [Signup for Free](https://m3o.com) or send us some [feedback](mailto:contact@m3o.com). 
Reach out on [slack](https://slack.m3o.com) or [twitter](https://twitter.com/m3oservices) if you have any questions.


