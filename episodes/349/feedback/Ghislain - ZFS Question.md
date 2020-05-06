
 i am sure you are longing for a ZFS question so here it is 

 I have 4  spinning rust disks  and 2 little 240Go ssd. This server will host several LAMP/FAMP guest running linux+lxd or freebsd+bhyve guest. To have the best performances while having failure of one disk proof system , should i use one ssd for log, one ssd for cache and the rust for data. Use the 2 ssd in raid1 and 1/2 for log 1/2 for L2ARC cache ? Will the L2ARC and ZIL Log compete for the IO and therefor slow down ?

  ZIL is for write and L2ARC more for read (but you have to write to the cache to start with so... Also will the write to the l2ARC also write to the ZIL doing double writes ?


I wonder what would be the best use of those 2 bonus ssd.

best regards,
Ghislain.