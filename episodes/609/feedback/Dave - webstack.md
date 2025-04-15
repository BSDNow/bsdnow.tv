Dave - webstack

TLDR there is nothing that I cannot make more complicated than necessary.

To serve my humble single-page website, https://skunkwerks.at/ I have developed a veritable labyrinth of a stack.

When a user requests my incredible single page static site, we of course look up skunkwerks.at in DNS. My DNS.

A DNS server that I wrote myself, because I can, in an obscure functional programming language called Elixir. The DNS server looks up its records in a database, Apache CouchDB, which is another well-known open source project that I have been contributing to longer than pretty much anything else in my life except drinking beer and skiing.

One DNS server alone is simply not enough, as you all know, so I have a cluster of 3 nodes in different autonomous networks, and using the lovely dnsdist.org DNS load balancer in front of them, again just because I can. I did not write this amazing software either, and it probably also deserves a hug.

Of course, one database alone is simply not enough, as you all know, so I have a 3 node CouchDB cluster, running in jails, on a FreeBSD 15.0-CURRENT kernel, on separate servers, on geographically distributed nodes within Europe. Because fault tolerance, for my 0.1 users/hour website.

In front of each couchdb node is an haproxy HTTP load balancer, so that every DNS server is transparently dispatched to the closest (in time and space) couchdb node that is up and ready for requests. I did not write haproxy, but if I could hug it, I would. I love haproxy.

There was something about a web page. Ah yes, my web page. From the amazing world of fault tolerant services, clustered databases and homegrown DNS servers, we now enter the non-fault-tolerant world of my home office and its garbage internet.

After our packets find their way across the internet, they eventually are confronted with my ISP-provided router. It's complete garbage, but they require me to have it, so its configured in transparent bridge mode, and hands all the packets off to a Traverse Ten64 router, which is a nifty tiny 8-core arm64 router, with 32GiB of ECC RAM, running FreeBSD 15.0-CURRENT, and it runs many many jailed services on it, but mostly it runs pf(4) and does the firewalling and garbage cleanup that my ISP, a large company, seems unable to do.

The obvious thing would be to run the webserver directly on the router, but as you are likely suspecting now, this is very unlikely.

I (of course) run ... another load balancer. It's haproxy again here, doing TLS termination, but for an added twist, it runs in a jail.

So inbound web traffic arrives via the firewall, is dumped into a jail, where haproxy provides the port 443 TLS encryption, and decides where to route most of the traffic.

Normally, my desktop is also up and running, so haproxy sends the traffic to a jailed instance of www/h2o, a web server that no longer even has official tagged releases, just periodically I update the snapshot from github, and re-deploy it.

But, dear reader, what happens if my desktop is down? Well, the obvious answer is that, as it runs FreeBSD 15.0-CURRENT, this can only be the case if it's being rebooted to run a new kernel, or if I am away on holiday and want to save some power.

In that rare case, haproxy on the router load balancer, will serve a mostly-identical website, but without some of the exciting content that is not directly linked to on the website, but is available to those who are in the know.

I mentioned encryption, and of course I use the now-commonplace Let's Encrypt ACME protocol, with a twist. No, no load balancers, but I want wildcard certificates, so for this, I use DNS-01 validation (proof of ownership of a domain), via DNS. The DNS server I wrote back at the top of this absurd little essay does the trick nicely!

Of course, there are 1000s of ways this could go horribly wrong, and sometimes it has, but mostly it does what it should, without intervention.

A+
Dave
