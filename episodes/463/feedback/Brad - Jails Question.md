
Hello Benedict, Allan, Tom, and JT,

Long time listener of the show since before 2014. I enjoy all the information you guys pass along and look forward to each weeks episode.

As a home user I have been using FreeBSD for file storage and backup sharing out pieces of the datasets over samba, nfs , and iSCSI. But it has always running on the host server directly. It wasn’t until a few months ago that I started to play with FreeBSD jails. Since I’ve gotten more comfortable with it I have started to consolidate some things like web servers, database servers, and similar into my main storage server to better utilize its hardware and save some power costs having less hardware turned on. It also seems much simpler to just set back up the jails and PF config to move to a new host, or recover something bad in a jail from a snapshot, or even save time if I decide to re-install the host OS fresh. I have been thinking about jailing ALL of the things, but cannot find much good info about if its actually a good idea or not. I’m thinking about letting the host server manage my zfs pools of course then just let pf on the box direct all incoming traffic to jails running on the host while nulls mounting the needed datasets into the jails. I do this now for the internal web servers, but not sure about my other services. Are some considered no-no’s to jail up? I’m sure a lot of them “could” work, but am curious “should” you do it even if it is possible:

Samba
NFS
iSCSI
DHCP
DNS
wireguard (as a host for my family’s phones & laptops to connect back home)
Unifi controller


If it's ok or even suggested to run these jailed, can you recommend any sources to read up on for surprises I might encounter running as jails instead of on bare metal? Nothing other than wireguard will be public facing, not even the web sites. They are only needed for my family so we just vpn back to the house if we need to access it. 



Thanks for your advice in advance,


Brad.
