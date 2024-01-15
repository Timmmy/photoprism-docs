# Using a Content Delivery Network (CDN)

A *Content Delivery Network* is a distributed network of servers that can deliver static content to users around the world.

## When to use a CDN?

**Large Media Files:** PhotoPrism stores photos and videos that can be very large. A CDN can help speed up the delivery of these files to users.

**Global Audience:** If your PhotoPrism instance is accessed from different locations around the world, a CDN can help reduce latency and improve the overall user experience by delivering content from servers that are closer to your users.

**Many Users:** If your PhotoPrism instance is getting a lot of traffic, a CDN can improve application performance by reducing the load on your server.

![Network Diagram](https://dl.photoprism.app/img/diagrams/content-delivery.svg?classes=w100)

## Config Options

You can use the following config options to specify the URL of an external CDN and change the cache expiration time for thumbnails and other static content:

| Environment                  | CLI Flag            | Default | Description                                                 |
|------------------------------|---------------------|---------|-------------------------------------------------------------|
| PHOTOPRISM_CDN_URL           | --cdn-url           |         | content delivery network `URL`                              |
| PHOTOPRISM_CDN_VIDEO         | --cdn-video         | false   | stream videos over the specified CDN                        |
| PHOTOPRISM_HTTP_CSP          | --http-csp          |         | HTTP Content-Security-Policy (CSP) `HEADER` *plus*          |
| PHOTOPRISM_HTTP_CACHE_PUBLIC | --http-cache-public | true    | allow static content to be cached by a CDN or caching proxy |
| PHOTOPRISM_HTTP_CACHE_MAXAGE | --http-cache-maxage | 2592000 | time in `SECONDS` until cached content expires              |
| PHOTOPRISM_HTTP_VIDEO_MAXAGE | --http-video-maxage | 21600   | time in `SECONDS` until cached videos expire                |

## CDN Providers

### bunny.net

![Bunny CDN](https://dl.photoprism.app/img/website/bunny-cdn.svg){ class='md right' }
If you don't have a CDN provider yet, we can recommend [bunny.net](https://link.photoprism.app/bunny-cdn). This EU-based company has a cute name, but is a reputable provider with [excellent performance](https://www.cdnperf.com/), a wide range of features, and more than 20,000 customers including big names like Hyundai. We also chose bunny.net for our website and public demo as they are fully compliant with the GDPR.[^1]

Pricing starts at $0.005/GB and there is no minimum usage or monthly fee, so you only pay for what you actually need.

[Learn more ›](https://link.photoprism.app/bunny-cdn)

### Cloudflare

[Cloudflare](https://www.cloudflare.com/) works similarly to a [reverse proxy](proxies/traefik.md) and allows you to make a private server publicly accessible over the Internet. This means that users accessing your instance through their service will only see a single URL as if they were connecting directly.

You must therefore **not configure a CDN URL** for your site, as this may prevent the user interface from loading. Also note that their free tier [does not include video streaming](https://www.cloudflare.com/plans/), so there may be problems with video playback if you are not a paying customer.

[^1]: We receive a $20 credit when you sign up through our link, which helps us fund the project infrastructure. 