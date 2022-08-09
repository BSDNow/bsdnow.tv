G'Day, mates.

Thank you great podcast, I'm listening to it for years, never been disappointed. 
I use FreeBSD for decade and seems all FreeBSD questions for which I can't find answer by reading handbook, man page or quick look to source code are ZFS related. 
So I'm just sending questions like that  to BSD Now . Hear comes my today question.

I have single disk ZFS pool which is badly 90% fragmented  as I allow it do go 100% full couple of times.  I got bigger drive as replacement, and now planning migration. I what it also defrafment it while I'm migrating. 
I can see 3 approaches.
 1) create new pool, new dataset and just "cp" data across. This would definitely de-fragment data.
 2) create new pool and "zfs send | zfs receive" data across. I believe it should also de-fragment data. 
 3) Use "zpool replace" to replace old drive with new bigger one. It is easiest and fastest way to migrate to new drive. But I'm not sure will it defragment pool? 

Could you please confirm that my thought about 1) and 2) are correct and what will happen in 3)?  Is there are any other ways to defragment pool?

WBR
 TheHolm
