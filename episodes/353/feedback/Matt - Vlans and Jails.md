Hi guys,

Great show.  Like many others, I feel I should be putting in my due diligence prior to asking questions.  Luckily, you seek feedback and questions so much that you've convinced me to just ask, which is great because I don't know when I'll have time to research and test this concept on my own.

I find jails to be quite elegant.  At a high level, they're easy enough to understand, but getting into the weeds will sometimes produce questions that aren't easy to answer.  I hope you can help provide some clarity for how to approach what I'm interested in doing.

I've got multiple VLANs on my network with a pfSense router.  My home/secure/trusted network is VLAN 10.  It houses a PC or two, as well as Unifi managed switches and a Cloud Key.  My FreeBSD server is by itself on VLAN 50.  On the server, I've got jails for Bitwarden, BookStack, and others.  For their internet access, I have a cloned loopback device, meaning they're on a separate "internal" network, and there's a PF rule to NAT their outgoing requests.

What I want to do is create a jail to act as a backup (or substitute) for the Unifi Cloud Key.  The Cloud Key provides the management interface that links the Unifi switches together and assigns the VLAN/traffic rules.  The "problem" is that the switches and Cloud Key (or proposed jail) must all be on the same VLAN.

What I *think* I would like to do is send a VLAN "trunk" to the server.  The server host would have to tag all its outgoing packets with VLAN 50, and the Unifi jail would have to tag its packets as VLAN 10 (yes, I could also probably leave one of those as untagged and the other as tagged, but I'd prefer to tag it all).  This should work, right?

My questions finally.

1.  Does my approach make sense?

2.  Would the Unifi jail need to be a VNET jail?

3.  How do I add VLAN support?  Is PF involved?

Again, I really enjoy the show, so keep up the great work.

-Matt 