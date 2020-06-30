Hi Allan, Benedict, and JT --
I started listening to your show a few years ago, and really enjoy a new dose of BSD whenever an episode comes out.
I have pfsense running on a small fanless box as my home firewall / router. I have a second box with identical hardware which I'd like to maintain as a spare in case the primary fails.
Ideally the backup would have the same version of pfsense and its packages, but how to accomplish this. Doing a backup of the config xml file on the primary, and restoring it to the backup is easy enough. But it seems the backup box needs to be connected to the Internet to get updates for pfsense and its packages.
I could temporarily replace the primary with the backup to update pfsense and packages, but this seems a bit cumbersome. Can you suggest an easier way?

Thanks,
Karl Cunningham