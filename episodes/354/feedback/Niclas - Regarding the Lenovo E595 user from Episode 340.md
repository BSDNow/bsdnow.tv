Hi!
I listened to the latest episode (340) the other day and there was a person having questions about running FreeBSD on a Lenovo E595 Laptop, with an AMD Ryzen 5 CPU and Vega 8 GPU.  I'll try to answer some of the questions about that.

First off, the e-mail that is referred in the question is regarding an issue where a change in current broke (compile time) the drm graphics drivers.  This has been long fixed in the port.

Regarding the actual issue, it's very hard to know what's going on without logs, specifically dmesg from when the driver (/boot/modules/amdgp.ko) is loaded, as well as Xorg.0.log from starting X.

The submitter mentions that the trouble most likely is loading the driver that is causing the issues, "...having a really hard time to make amdgpu driver to be recognized in FrreBSD [sic]..."
I can't remember on top of my head, but it might be that this GPU is only supported by drm-devel-kmod, in which case the only way to have it running is to use FreeBSD 13-CURRENT.

In any case, it is probably easiest if this person asks for help on the x11@FreeBSD.org mailing list, including hardware information, a problem description and a dmesg and logs I mentioned earlier.

Regards 