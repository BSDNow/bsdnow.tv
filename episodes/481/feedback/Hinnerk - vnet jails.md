Hello Benedict, Allan, Tom and JT,


thank you for the show and all the great information.

I'm writing to you with a question that seems like it should concern more people but I wasn't able to find a good answer.

I have some root servers in a data center and run FreeBSD on them (actually its HardenedBSD, but I guess that doesn't matter).

I have a bunch of jails on each of them and also want to run some bhyve VMs. If I try to use VNET-Jails or bhyve VMs by default a bridge device is created. This leads to the data center operator seeing MAC-Adresses from the VNET jails or the VMs on "my" switch port and warning me to cease that behaviour or otherwise be shut down.

Is there a way to use bridges but keep the internal MAC addresses from 'leaking' or a default way to connect VNET jails or bhyve VMs without a bridge and just route the traffic via the main physical interface(s)?


Thank you and keep up the great work.

Hinnerk 