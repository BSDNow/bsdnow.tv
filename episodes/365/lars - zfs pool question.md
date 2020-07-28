Hi guys,

am a listener since episode 1 and still love the show!

I have a ZFS zpool upgrade question:
I just read that when you upgrade a ZFS zpool with 'zpool upgrade -a
<poolname>' and you boot from <poolname>, you have to upgrade the bootcode
as well (i.e. with '# gpart bootcode -b /boot/pmbr -p /boot/gptzfsboot -i 1
ad0'. 
My question: when <poolname> is a ZFS mirror of 2 disks, do you have to
upgrade the bootcode on both disks or just 1 disk?
Thank you in advance for answering this one!

With kind regards,