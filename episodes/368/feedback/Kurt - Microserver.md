Hi Benedict and Allan,

I have an old HP Microserver that I've been running FreeNAS 11.x on for a while now.  It's not a critical backup, just something to play around with on my eventual journey to adopting FreeBSD (we're a Mac household now, and I'm running ZFS as my primary user filesystem under Mojave 10.14).

I've always had a policy of encrypting all disks, so I use either FileVault (on Mac boot drives) or ZFS native encryption (on home directory and on small portable replication target drives connected via USB3).  The FreeNAS box was different, however; the 11.x releases of FreeNAS don't support ZFS native encryption, so I selected the GELI encryption option for my FreeNAS disks.  That turned out to have some pretty serious performance implications, because the little HP box has an AMD Turion processor that is roughly equivalent to an Intel Atom, and lacks AES instructions to speed up encryption.  It sits down in the basement on a Powerline ethernet adapter that passes data at sub-USB2 speeds, and it can't even keep up with that!

I recently read that TrueNAS Core is coming out soon (beta is out now) and it includes the updated ZFS support for native encryption.  I'm thinking that this could be a godsend in my situation: it should be possible to send the encrypted datasets directly from my computer in raw form, and have the HP just accept them without decrypting them, right? Since the HP won't be decrypting data as it comes in it should have all of its processing power available for handling the network and shoving the bits onto the disks.  Then, if I have some unusual need to get at the data on the HP in unencrypted form I would just load the keys on the HP, and now TrueNAS Core/ZFS will decrypt on the fly (with the usual attendant performance lag).  Of course this will require a complete wipe of the HP box and its current disks, but that is OK since it is only backup data.

What is most fuzzy for me in this situation is key management, so I wonder if you could point out some workflows and pitfalls around managing the keys in this situation.  Right now my only key management task on my main computer (and on the replication targets) is to simply issue the command

% zfs mount -l TANK

Also, I wonder if TrueNAS is going to be happy to have a dataset that is going to be in the encrypted and not mounted state most of the time.

On another topic, do you think you'll (Allan) be eventually updating your Advanced ZFS book to include information on native encryption (and possibly other advances)?  I already have two copies of the books; I initially bought the Kindle editions, but then found that I used them so much that I wanted paper copies!  So I guess I'm ready for a third copy of the Advanced book, if you should update it.

Thanks for all the interesting BSD info.  I enjoyed hearing you (Allan) discuss ZFS on the Ask Noah podcast, too.

Kurt 