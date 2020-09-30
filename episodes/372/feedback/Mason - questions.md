In the latest show, on Linux "apropos battery" finds the acpi(1) man
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

