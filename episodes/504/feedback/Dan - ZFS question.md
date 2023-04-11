Hi Allan and Benedict

I was getting concerned you might be runnng low on ZFS questions so I thought I'd step in and help combat any potential drought.

I recently had to restore a ZFS based server with about 800 home dirs, each with its own dataset, when most of the directories got deleted somehow. I ended up restoring them all from scratch using syncoid which took over four days.

What I would've liked to have had when I noticed all the home dirs were missing was a script to automate rolling back all of the datasets within the /home dataset by a given amount. I use sanoid to create the snapshots so it would have to support rolling back snaphots created using sanoids naming format.

I can probably write this myself but I'd prefer to use an existing, tested script if such a thing exists. Are you aware of such a script?

Great to see the show is still going after all these years!

Thanks
