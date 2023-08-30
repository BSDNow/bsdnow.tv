Hey BSDNow folks,

You asked for more questions and feedback, so here I am again.

The first thing I want to talk about is what I and others in the FreeBSD community (like vermaden in a recent post) have noticed lately, which is that one of FreeBSD's most amazing features, VNET jails, is rarely talked about, and is still not covered at all in the FreeBSD Handbook. This comes as a surprise to me, as I regularly hear people complaining about how complex networking, especially IPv6, is in Docker. This is a missed opportunity, as networking in a VNET jail is very easy, as it is identical to how it is set up and works on a regular FreeBSD host. Personally, there is not much I can do here, but maybe someone else will hear about this and decide to take matters into their own hands.

Speaking of networking, I recently tried IPv6 with SLAAC on FreeBSD hosts and VNET jails, but what I could not figure out was why I could not get rtsold to install an IPv6 default route unless I rebooted the host/jail. Online I have also found others asking why this doesn't work in several places, but have yet to find a solution. With IPv4 and DHCP, this is not necessary, and at this point I don't know if this is a bug or if it's by design. But what do you think about this?

Thanks and keep up the good work.

Felix
