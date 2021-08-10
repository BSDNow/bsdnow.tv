G'Day, Allan, Benedict and JT.  

First, In response notion of sad situation with Ethernet ports on modern laptops one of you guys mention in episode 377 I have to mention that proper Ethernet ports are nor completely gone from modern laptops.  I recently got Lenovo T15, and it has build-in Ethernet. I run Linux on it with root on ZFS and native encryption. And it runs great. Which brings me to bunch of ZFS question.
I in using  ZFS with FreeBSD for probably a decade, but it was always "proper" server setup with RAID or mirror vDEVs and ECC memory.  With only single NVMe drive in my laptop ZFS is setup there with single disk VDEV. 

So, question number is: how to use ZFS in this setup to protect from bit rot? I see 2 ways
  1) set copies = 2 on zpool. But it haves disk capacity
  2) Split disk to multiple partitions, and build raidz on them. Performance will be terrible. 
Is there any other way to achieve bitrot protection on single disk?

Question2:  It seems there is widespread opinion that ZFS should be only used with ECC memory. In my case 20Gbs of ARC data are sitting in memory for weeks, data my get corrupted as (from my best knowledge) ARC is not protected by checksum.  What is your opinion on this matters? How safe is ZFS without ECC.

Question3: I put my music collection (which is quite static) on "permanently" plugged SDCard formatted as ZFS . Not a typical usage case for ZFS.  SDCard can be easy wear off by writes friendly, so zpool was configured with "atime = false" to minimise writes under normally read-only usage. Output from "zpool iostat" confirms that nothing is getting written to SDCard pool. But I'm not sure that iostat shows everything. Is there anything else can be done to minimise unnecessary writes.   

Pure theoretical Question 4: .  Imagine mirror VDev with one SSD and one spinning disk. What performance of such asymmetric mirror is expected to be?
IMHO on writes it should be slow as single spinning disk, but on reads it should be as fast as SSD + bit more?  Does ZFS waits ( or even query ) for data from both disk in mirror if one disks already returns data and checksum is right. 

Thanks in advance.  And you show is great ( but I guess you already know it) 
