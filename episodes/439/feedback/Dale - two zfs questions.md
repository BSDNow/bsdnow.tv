Hi guys, first thanks for a great podcast! 

I recently build a new x86-64 server and took the opportunity to jump into zfs. The old server was a cast-off dual-core HP busness desktop with a single ufs system drive and another ufs drive for storing backups. The new server is a slightly newer castoff (quad-core dual-thread!), installed two 1TB SSDs and installed FreeBSD 13 in "zfs on root", mirroring the SSDs, and no encryption. The server is operated headless, I do not install a GUI desktop or GUI apps.

I have two questions related to my now using zfs.

1. If I break booting somehow, how do I boot the system to correct whatever I did wrong? I used to be able to boot from a FreeBSD DVD, does this still work? Fwiw this was usually after I upgraded virtualbox-ose using pkg and forgot to recompile the kmod from source (although this specific issue seems to be fixed now).

2. How do I recover when one of the SSDs fails? Do I just put in a new SSD and magic will just happen? 

Thanks again, and Merry Christmas!

Cheers, Dale