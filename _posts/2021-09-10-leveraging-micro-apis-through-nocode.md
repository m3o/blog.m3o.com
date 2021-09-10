---
layout: post
title:  "Leveraging Micro APIs through NoCode"
date:   2021-09-10 10:00:00
author: Dominic Wong
author_url:     'https://github.com/domwong'
---
<br>
Over the last few years the "NoCode" movement has gathered huge momentum; today, there is a plethora of tools that will empower non-developers to turn their ideas in to real businesses. 

Micro was founded on similar principles of lowering barriers to entry for building complex systems. We do that by packaging up useful logic in to APIs, that we serve on our platform M3O, that can be used as building blocks to help you build your vision more quickly.  

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/epichandshake.jpg" alt="epic handshake meme, micro and nocode movement together making coding easier"/>
<br>

We're excited to make this alignment of goals more concrete by offering some of our APIs as plugins on [Bubble](https://bubble.io), one of the leaders in the NoCode space. You can see all the plugins we currently offer on our [contributor page](https://bubble.io/contributor/micro-1630667285143x793772307354948700) and we'll be adding more over the coming months.

## Building a weather app
As an example of what you can create using the Micro APIs let's build a new Bubble app to display the weather forecast.

Start by creating a new blank app

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/startblank.jpg" alt="blank bubble app"/>

Now let's install the [M3O Weather plugin](https://bubble.io/plugin/m3o-weather-1630678945170x949065629197664300)

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/plugins.jpg" alt="bubble plugin list"/>

We'll need an API key to enable access to the weather data so we'll sign up for an account on [m3o.com](https://m3o.com/register). Once we're signed up we can grab a key to use from the API keys page, either using the personal token or creating a new API key. Take this API key and plug it in to the corresponding text box on the bubble editor making sure to prefix the key with the string `Bearer ` e.g. `Bearer 123456789abcdef`. 

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/plugin-with-key.jpg" alt="m3o weather plugin with key"/>

Back to the Design tab and we'll add a repeating group to display our forecast, putting each day in a different cell of the group. We'll fill out the settings of the repeating group as follows:
- Type of content - Forecast forecast (M3O)
- Data source - Get data from an external API -> M3O weather - Forecast
  - `num_days` - 5
  - `location` - London (or wherever you want your weather)
- Rows - 1
- Columns - 5

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/repeating-group-settings.jpg" alt="settings for repeating group"/>

Now we have a repeating group that pulls in data from the weather API we need to display this information. Drag a Text element on to the repeating group and in the text box click on 'Insert dynamic data' -> 'Current cell's Forecast forecast (M3O weather)'. You'll see a list of all the fields available to display from a weather forecast. Add the ones you want to see.

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/insert-dynamic-data.jpg" alt="Displaying the API output using the dynamic data facility"/>

If you hit preview you'll see we now have a page that displays the weather forecast for the next 5 days. But it looks a little bland, it could do with some jazzing up. 

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/preview-boring.jpg" alt="Preview of the app but it looks a bit boring"/>

Thankfully the weather forecast API includes an icon to describe the conditions. Let's add this as an image. Drag an image element on to the repeating group and we can set the 'Dynamic image' field as follows. Note: the image is available in the API under the field `icon_url` but the URL does not specify http or https so you'll need to decide which you want to use and then prefix this field with either `http:` or `https:` as appropriate (see screenshot for example). Click on 'Insert dynamic data' -> 'Current cell's Forecast forecast (M3O weather)' and choose `icon_url`. Your settings will look something like this; note I've added the forecast's `condition` field as alt text to be more accessibility friendly.  

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/weather-image.jpg" alt="Adding an image to the weather forecast to jazz it up"/>

Hit preview again and now you'll see a much more appealing site.

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/preview-with-icons.jpg" alt="New and improved weather forecast with images"/>

The great thing about APIs are that you can treat them as building blocks, combining them to make bigger and better things. Why don't we add something else to make this site a little more useful? Rather than hardcode the location we can approximate where the user is located based on their IP address and display the weather for that location. Handily, another API that we offer is the [IP geolocation API](https://bubble.io/plugin/m3o-ip-geolocation-1631116195387x494006979451682800) which helps you to map IP addresses to actual geographic locations. Let's add this plugin (just search for 'M3O' in the plugins tab) like we did with the weather plugin. One of the advantages of the M3O platform is that a single API key will give you access to a wide range of APIs which makes management and billing much simpler. Copy and paste the API key from the weather plugin in to the IP geolocation plugin. One final plugin that we'll need for this demo is 'ipiphy' which is a Bubble plugin that gets the user's IP address.

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/three-plugins.jpg" alt="Three plugins installed"/>

Back to the Design tab let's add a Group element to handle the IP location data. We set the following:
- Type of content - Lookup (M3O IP)
- Data source
  - Get data from an external API -> M3O IP - Lookup
  - ip - Get data from an external API -> Get current user's IP address

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/ip-lookup.jpg" alt="Settings for looking up IP address location"/>

This will load location data for the user's IP address in to the group. We can add a text box to the group to display some of the user's location data; we'll add the city and country. 

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/location-information.jpg" alt="Displaying location information retrieved from the API"/>

Now the final step is to use this location as the input to our weather forecast. Click on the repeating group and let's update the data source. To use our location retrieved from the API to an address for the weather forecast we use the 'Calculate formula` facility in Bubble. Click on the repeating group's data source and under location choose Insert dynamic data -> Calculate formula -> 
- Type - Coordinates to Address
- latitude - Group Lookup (M3O IP) -> Lookup (M3O IP0) -> latitude
- longitude - Group Lookup (M3O IP) -> Lookup (M3O IP0) -> longitude

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/ip-location-weather.jpg" alt="Updated settings for repeating group using the location from the IP API"/>

Once we've made the updates we can go back to the preview and we see a weather forecast automatically personalised for the user's detected location. Note: this won't work in all cases e.g. if the user is using a VPN or similar. 

<img style="object-fit: contain" src="{{ site.url }}/assets/images/2021-09-10/finished.jpg" alt="The finished demo app"/>
