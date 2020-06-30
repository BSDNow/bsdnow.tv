Hi, Benedict and Allen!

I have been a FreeBSD user and fan for over 6 years now, many of my reasons why can be attributed to this great podcast 

I run a small home network, at the heart of it is a Dell T110 running VMware ESXi. The VMware server hosts the following VMs, all running FreeBSD:

- VM1 - PFSense VM acting as my home router/firewall
- VM2 - Plex server
- VM3 - Remote access server I use to SSH into my network remotely/ create SSH tunnels
- VM4 - A Utility server that runs various tools, such as Transmission, Sonarr, and an OpenVPN client

The ESXi server has 3 physical NICs; Two of the NICs are bonded into a static port-channel configured as a trunk to a Cisco 3560 switch, the third NIC is plugged straight into my ISP modem as an access port. On the ESXi server, the port-channel is tagging packets for various VLANs (public WiFi, streaming devices, servers, etc...) into separate vSwitches, which are in turn fed to the PFSense VM as separate virtual interfaces, while the 3rd NIC is handed directly to the PFSense VM to grab a public IP directly from my modem. The other VMs are nothing special.

For the most part this set up works perfectly fine. However, I have been looking at replacing the Dell server with more modern, capable hardware to allow me to host more VMs. Also, as comfortable as I am administrating the ESXi server, I have been playing a bit with bhyve on a physical FreeBSD test machine I have and have found it fairly easy to build and manage VMs using iohyve. I would also like to be able to snapshot these VMs using ZFS and backup those snapshots to my FreeNAS Mini.

So here are my questions:
- Do you believe bhyve is stable and mature enough to be run in a production environment and capable of replacing VMware ESXi?
- Is it possible to easily duplicate my setup in bhyve, specifically my PFSense configuration?
- Is iohyve your recommended method of managing/ creating virtual machines for bhyve, or could you offer a better, easier solution to manage these VMs?
- What are your thoughts on running FreeBSD on bare-metal systems using AMD Opteron CPUs? The new server I'm looking to purchase is an HPE microserver Gen10 that features this type of CPU.

Thank you for your help and your wonderful, insightful podcast. Cheers, and happy post-FreeBSD day!