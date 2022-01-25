Hi team,
I have an ESXi server with, among other OSes, about 17 FreeBSD VMs.  Each VM is performing some specific function or resides in some security zone.  I have a VM for my TOR relay, database servers, DNS server, web server, SMTP mail-hub, external mail server, external reverse proxy, syslog receiver, network monitor, forward proxy, etc.  The three or four security zones I have are separated by a router performing simple packet filtering.
I am considering using jails to virtualise these functions and collapsing them onto a single FreeBSD VM rather than individual VMs and would like your opinion on the following:
- will the overall memory use on the ESXi host decrease?
- will the CPU usage on the ESXi host decrease?
- what version of FreeBSD should the jail host run?
- what kind of jails do you recommend?
- what file system should the jail host run?
- how best should I maintain currency of both the host OS and jails?
- should I use VNET?
- what jail manager, if any, should I use?
You mentioned recently that you were looking for questions so I thought I send you a big one!
Many thanks for your efforts in making this podcast; the community benefits greatly.
