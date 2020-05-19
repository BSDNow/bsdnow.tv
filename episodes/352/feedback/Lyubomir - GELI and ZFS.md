 Dear Allan, Benedict and JT,

Thanks for the nice podcasts. I find a lot of interesting things on bsdnow.tv. I have some questions for you.

1. I have a laptop with one SSD. I have installed FreeBSD 12.1 with ZFS and GELI. These days I decided to move the installation to a bigger SSD. My first thought was to copy the data with dd but I have heard that encrypted disks do not do well with dd. I tried cloning the disk with a disk duplicator (an ORICO external sata-to-usb docking station) but with no success. On reboot I get:

gptzfsboot: no zfs pools located, can't boot

I searched the net for any solution to this but all proposed I could find (to repair with gpart, to "enable" the GELI partition with "geli configure -g", etc.) did not helped. Do you have any idea how to quickly clone an SSD with ZFS and GELI?

2. I tried to "zfs send / zfs receive" the whole data from the source SSD to another machine, where I have enough storage with zfs send / zfs receive. On the receive side I wanted to have the data in certain dataset (e.g. zroot/temp/from_ssd). But I had a problem. On the sending side the pool is named "zroot" and on the receiving side it is the same. On the receiving side it asked to replace the existing datasets. Where did I go wrong?

3. One proposal for the podcast. Can you please invite more BSD developers to tell their story how they started with BSD and possibly to give advise how to start coding with BSD (different coding languages). I hope it will influence younger people to start using and contribute to BSDs.