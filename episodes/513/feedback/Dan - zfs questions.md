Hi BSD now crew and listeners

You may recall I wrote into your feedback section recently regarding the several hundred missing ZFS home dirs that I resorted to fully restoring from a remote backup instead of rolling back?

The reason I didn't perform a ZFS rollback in a for loop like Allan suggested is because I discovered, when I needed to do this, that I had slightly misconfigured sanoid. Jim Salter pointed out my config error.

In order to be be able to successfully recursively roll back nested datasets without clever scripting to process dates, you must configure your sanoid.conf backup policy to use recursive=zfs instead of recursive=yes as I was using up until this happened.

If any of your listeners want more details on configuring sanoid correctly for doing nested rollbacks they can read my discussion of this with Jim Salter on github at https://github.com/jimsalterjrs/sanoid/discussions/804

Thanks
