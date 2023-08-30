Just dropping a quick note because this is actually something we did ourselves recently. I’ve actually done this twice: once at a former employer who did video streaming and again at Stadia Maps.

As you said, at least in some cases, the CDNs are really just built on major cloud vendors. In our case, we chose Linode (now acquired by Akamai) and built an edge network using HAProxy for our ingress along with some caching layers.

Everything depends on the project needs, but if you’re just trying to minimize time to first byte and you can afford to replicate your data across many regions, going with a provider that gives you a good deal on bandwidth can save a fortune.

We're at the complete opposite end of the spectrum from Netflix as a small company, but building your own CDN on top of a cloud vendor but your guess about “just Azure and getting bytes for cheap" is actually a totally logical approach in some cases ;)

Cheers,
Ian
