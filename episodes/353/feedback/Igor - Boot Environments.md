Hello Allan and Benedict!

I am a huge fan of BSD Now podcast, please keep the show rolling.

Since you often ask for questions on the air here is mine:

I run FreeBSD jail server in AWS cloud with ZFS on root. I want to utilize boot environments feature to safely try upgrading my system but the problem is that 
AWS cloud does not provide console access to the VM - so I can't really see bootloader screen and provide any input. (the only way to access the server is through SSH, which is not there at boot time)

Is there a way to use boot environments in such scenario? Something like "try booting this zfs snapshot once and if it fails revert back" feature.

Thanks!