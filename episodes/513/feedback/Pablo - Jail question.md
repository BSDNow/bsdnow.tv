Hey guys, happy National Wine Day!

Thank you for the great show as always! Great interview with MWL on
episode #507.

Got a jails question. I have setup vnet/vimage jails and noticed
/dev/pf is not being exposed to the jail. Found the doc below which
led me under the impression that it should have been exposed by
default (I am running latest 13.2):

https://reviews.freebsd.org/D26537

I even added  "devfs_ruleset=5;" under the jail definition (restarting
it after) and i still don't see /dev/pf exposed.

Anything I am missing? Trying to deploy pf inside the jail itself.

Thank you

Paulo


