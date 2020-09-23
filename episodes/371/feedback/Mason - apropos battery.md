I've waited patiently for about a month since I sent this, so I'm resending
this now in hopes of an answer. I'll also email freebsd-fs@freebsd.org
since I really do want options.

Also, re: the latest show, on Linux "apropos battery" finds the acpi(1) man
page. Rather than adding a "battery" man page to FreeBSD, it might make
more sense to make sure that the apm(8) man page comes up when someone uses
the traditional Unix "apropos" command to find relevant resources.
Comparison:

---------------------------------------------------------------------------
APM(8)              FreeBSD System Manager's Manual (i386)              APM(8)

NAME
     apm – control the APM BIOS and display its information
---------------------------------------------------------------------------
    vs.
---------------------------------------------------------------------------
ACPI(1)                     General Commands Manual                    ACPI(1)

NAME
       acpi - Shows battery status and other ACPI information
---------------------------------------------------------------------------


Anyway, my question:

On Sun, Aug 02, 2020 at 11:56:35PM -0400, Mason Loring Bliss wrote:

> I forget if there's another address for questions now, but this appears to
> be the last one I used, so:
>
> I'm migrating a mail server to a FreeBSD jail, and I've seen conflicting
> notes about how best to tune ZFS for holding accounts with Maildirs. My
> current thinking is that I don't want to change recordsize as it's an upper
> limit, not a minimum, but that I might want to set primarycache=metadata so
> I'm caching information about Maildir contents, but not the Maildir
> contents themselves. But are these valid thoughts, and what else is there
> to think about? The problem is that I don't know what I don't know, and I'm
> not sure about what I do know, so I'd love some advise about how best to
> tune a dataset for Maildirs.
>
> Thanks!