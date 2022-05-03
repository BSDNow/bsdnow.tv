Hi guys,

I really enjoy the show!

A big Thank you to Tom for his home lab story in episode 447 I think?
It was great to hear an idea of the sort of hardware that will work for a home FreeBSD system.
And it would be great to hear from other BSD users what is working for them, as Tom outlined in the episode.

My current attempt is to use a NomadBSD Live usb memory stick on my old white macbook, 
but I’ve hit a problem with efi boot and loader.lua: invalid argument. I’ve outlined below

Being this is an image of Nomad BSD is there a way to correct this, or a command I can type to move the booting forward?
I don’t have any other version of freeBSD running to swap a file from an earlier version like I’ve read elsewhere. 

Many Thanks
Glenn in Adelaide South Australia


```
Consoles: EF1 console
Reading loader en vars from /ef1/freebsd/loader.env
FreeBSD/amd64 EFI loader. Revision 1.1

 Command line arguments: loader.ef1
 Image base: OxabBae000
 EFI version: 1.10
 EFI Firmware: Apple (rev 1.10)
 Console: ef1 (0)
 Load Path: HD(3,GPT,28271899-ad2f-11eb-bBca-541ad50e5bf,64800,6eb800)
 Load Device: Pc1Root (8) /Pc1 (1.4) /USB(B,8) /HD (1.MBR,88,20,307ffe0) /HD(3,GPT,28271l
 BootCurrent: 0000
 Bootorder: B088
ERROR: cannot open /boot/lua/loader.lua: Invalid argument

Type '?' for a list of commands, "help' for more detalled help.
OK_
```

I can issue a power off command which works, but I’m clueless where to go from here.
Do you any of you have any ideas?

Cheers
Glenn.
