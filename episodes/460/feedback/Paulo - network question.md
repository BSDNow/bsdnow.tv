Hey guys, happy national barbecue day!

Thanks for the amazing show you guys put week after week, always great to listen to!!

I do have a couple questions hoping you could help me out.

On the freebsd 13.1 release notes NFS changes section i see the following:

"A sysctl called vfs.nfsd.srvmaxio has been added that can be used to increase the NFS server’s maximum I/O size from 128Kbytes to any power of 2 up to 1Mbyte."

Would it be interesting from a performance perspective to have this match a particular ZFS dataset recordsize (when larger than the default 128kb) exposed via NFS - or this is not the problem this sysctl new maximum value came to solve? 1Mbyte is the maximum recordsize on ZFS and that's this new sysctl maximum too now.

Last question on wifi support - is there any particular 802.11ac chipset fully supported on latest freebsd?

Thank you

Paulo
