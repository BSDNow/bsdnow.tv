Hi,

Just heard the latest episode, in which you mention ISC DHCPd being deprecated and replaced by ISC Kea.

Kea is pretty nice, and runs fine on FreeBSD (and probably the others as well, just tried on FreeBSD). It's configured in JSON which is what it is, but it has an API, can run i HA mode, be backed by databases (or just a plain text file) rich documentation and a bunch of 'premium' extensions aimed for large enterprises. These paid for extensions seems to be a way to guarantee some basic income from the project, and I think it's OK.

I wrote an ansible role to manage kea (https://github.com/oscarcarlsson/ansible-role-kea), so I can write YAML instead of JSON. I described the precursor for this role at my blog, https://www.monotux.tech/posts/2021/09/kea-ansible-freebsd/

Anyways, thanks for a great show!


Cheers from the sub-arctics,
Oscar
