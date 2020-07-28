I run ZFS on my laptop an I would like to keep a complete backup of the
storage in case it ever breaks.  I already backup my home directory to
an external machine but I'd like to keep the full backup on a portable
hard drive as well.

I'm wondering what the best way to do this is?

- Should I add the portable HD as a mirror and run as degraded whenever
  I don't have it plugged in?  And just let resilvering update to the
  latest?

- What would the restore procedure?  If I'm doing a new FreeBSD install,
  would I just drop down to a shell and add the new laptop as a mirror
  and resilver it over?

- I never feel comfortable adding the bootcode (when I upgrade zfs) and
  I assume I would need to after the resilvering is complete to be able
  to boot again, is that correct?  Is there an easy way to think about
  adding bootcode that I can feel comfortable I'm not overwriting actual
  data?

Thanks!