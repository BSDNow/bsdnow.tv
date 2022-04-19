
Hello Benedict, Allan, Tom and JT

First of all I like to thank you all for this great podcast. I started to listen in summer 2019 and didn’t missed an episode since then.

With little to no knowledge of UNIX, BSD or any kind of shell, I thought it was a good idea to replace my standard NAS with a system that provides ZFS, just to have the best filesystem for my family photos. I built my own server, installed FreeNAS and realised very fast that I would have to learn a lot. My setup covers now a TrueNAS main server, with a backup server at a second location and over 80TB of redundant pool space. For most listeners probably peanuts, but for an amateur system still not too bad.

The first jail was for Nextcloud and at this point I like to thank Samuel Dowling for his great Nextcloud jail documentation. It helped me a lot to dive into the world of BSD and not just taking the easy way of using a standard TrueNAS plugin. Through his guide I got a free reverse-proxy on top of it. Later followed more trivial stuff like Plex Server, Vaultgarden Bitwarden, Adguard and an UniFi Controller.

Many smaller and bigger challenges later I have feedback and questions.

First the feedback to the beginning of Alans story last week. I ran into the same mac address problem and had to invest many hours to solve the riddle. With iocage I exported, renamed and imported my Nextcloud jail to have a second instance. Both jails were running under different names but with the same vnet0_mac property. With amateur debugging skills it was hard to figure out, why each instance was randomly accessible or not. I hope your story will save people in the future a lot of time.

And now to my question: Since my time and skills are limited, I prefer to use the replication task manager of TrueNAS and send regular snapshot to the backup server. I had to learn, that a non-root backup user needs certain ZFS filesystem rights to handle the receiving part on the backup server. The initial backup worked always but all following replications failed, since something went wrong with the rights. After changing the SSH user to root, as described in the TrueNAS documentation, it worked. How reasonable is it, to have root SSH active? What are your recommendations to limit the risks coming with such a setup? What is the best secure way of backing up one system to another?

Thank you very much
Ben
