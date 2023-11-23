
Howdy, gents,

First, welcome to the show, Jason.

I have a quick question about allocating disks in a zpool when you have a "considerable" number of drives. I have several TrueNAS boxes at work, and we just received three more units that should be coming online in the next few weeks.

Traditionally, what I have done is to set up my pool, say of 60 drives, in 10 6-drive RAID-Z2 vdevs (when I initially did it, I was using 6 10-drive vdevs, but found this to become problematic over time). I would then arrange those 10 vdevs into a RAID-Z2 for my actual pool. The absolute redundancy has stood me in good stead.

However, I started thinking that perhaps this is overkill? Would it be better to do 10 6-drive RAID-Z1 vdevs and then do the pool as a RAID-Z2? Or perhaps make the vdevs RAID-Z2 and the pool RAID-Z1? Or should I just keep doing what I'm doing? I want a reasonable amount of redundancy for data protection, but I feel like I am leaving additional storage space on the table. What is best practice for something like this?

Thanks,
--b
