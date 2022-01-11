


Hello. Enjoying the show. 

In episode 432 you asked for questions. Since you asked for it, here's a question I've been holding onto. Let me preface it by saying that I've seen posts of people quite happy with ZFS on NetBSD, so audience members shouldn't conclude anything from my problem about how mature NetBSD's support is. Oh, also, their kernel gives the message "WARNING: ZFS on NetBSD is under development" at startup, so there's that too.

I'm running 9.2 stable on an Elitebook 8440p with 4 GiB and a 5400 rpm spinning disk, also not of recent vintage.   I have a 108 GiB zpool on one of the disk's slices that I use for home but also for /usr/pkgsrc and /usr/pkg.  Quarterly, I update pkgsrc using cvs and find it to take a surprisingly long time. It's an old underpowered machine but still not heavily loaded when I run these updates. Usually I have less than 1 GiB memory active and the cpu is mostly idle. There's really no reason for me to have a machine newer than 10 or 15 years.

During updates I notice that the state of the cvs process in top is usually zfscv/2 (maybe sometimes zfscv/3 or another number). When I run ktruss against cvs the slow syscalls appear to be unlink, rename, and rmdir. These calls generally take from 60 to 200 milliseconds per file/directory.   Maybe this is when cvs updates its many CVS subdirectories.

So I wonder what your reaction to a 200 millisecond rmdir is? This can't be normal.

zdb shows my ashift to be 9. From the time I first installed NetBSD 9.0 to some more recent update I've noticed the new message in zpool status output: "One or more devices are configured to use a non-native block size. Expect reduced performance."  But I thought Allan said in a recent episode that that's likely not a big cause for concern.  It's a little weird too, cause smartctl shows the drive's logical sector size to be 512, but, yes, it also lists the physical size as 4096.

zdb shows a version number of 5000. I don't use dedup. /usr/pkgsrc is on its own filesystem within the pool and the pool has 28 GiB available. zpool list shows 48% fragmentation.

Any thoughts? Otherwise, what should be my next steps trying to understand this behaviour. I feel like I need to become more knowledgeable before bugging the NetBSD community, who (unlike you guys?) may not benefit much from more questions from the lazy and uninformed.
