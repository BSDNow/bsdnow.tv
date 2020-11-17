Greetings Benedict and Allan

Thanks for the great show, I really look forward to it every Thursday
when it becomes available on my podcast player.

I have a question was hoping you guys could point me into the right
direction. I am trying to get FreeBSD up and running on a Bananapi
M1plus arm device. I tried different versions and they all wont finish
booting. On 12.x it stops booting after the following message is print
on the screen:

Hit (Enter] to boot immediately, or any other key for command prompt.
Booting [/boot/kernel/kernel]...
Using DTB provided by EFI at Ox47ef3000.
Kernel entry at Ox74000180...
Kernel args: (null) EHCI failed to shut down host controller.

I tried 12.0/12.1/12.2 as well as the latest 13-snapshot and i can't
get it booted. I suspect just writing the image using 'dd' is not
enough (maybe some manual DTB file copy is required?).

Also tried 11.3 and 11.0 without luck.

One thing i noticed was a change from armv6 to armv7 from 11.x to 12.x
on the images filename, such as below, not sure if this is relevant or
not to the issue i am seeing.

FreeBSD-11.0-RELEASE-arm-armv6-BANANAPI.img.xz
FreeBSD-12.0-RELEASE-arm-armv7-BANANAPI.img.xz

Not sure if there's an install guide i completely missed? The wiki
page just shows what's supported:

https://wiki.freebsd.org/arm/Allwinner

Thank you and have a great weekend!

Paulo