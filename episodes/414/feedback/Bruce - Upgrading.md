
I was trying to go from FreeBSD 11.4-RELEASE to 12.2-RELEASE.  

I see that both are still supported as Tier 1 with amd64, so I thought it would be OK. (I have already upgraded other servers to 12.2 from 11.4 a month or so ago)

Anyway, I kept getting an error and did not know what else to try.  Can I wget the files?  I am able to ping update4.freebsd.org just fine.  These are all amd64 VMs.

------
uname -v
FreeBSD 11.4-RELEASE

freebsd-update upgrade -r 12.2-RELEASE -s update4.freebsd.org
src component not installed, skipped.

This may be because upgrading from this platform (amd64) or release (11.4-RELEASE) is unsupported by freebsd-update.  Only platforms with Tier 1 support can be upgraded by freebsd-update.  See https://wwww.freebsd.org/platforms/index.html for more info.

If unsupported, FreeBSD must be updated by source.

I get the same error if I try "freebsd-update fetch" or do not use the -s.

Thanks.
Bruce C
