
Hi

I finally got round to testing mfsbsd which seems like a good fit for my use case but I seem to have run into a little issue mounting my zpool.

The zpool never mounts upon reboot because it is always marked as being last in use on another system. ie. On a running mfsbsd system I issue a 'zpool mount -a' and nothing mounts. A little playing around with the system shows that my /etc/hostid is randomly generated on every reboot. Looking in /etc/rc.d/hostid, the script seems to be generating a random hostid because the function hostid_hardware() reads a blocked UUID from 'kenv -q smbios.system.uuid'. The blacklisted UUID picked up from hostid_hardware() is 03000200-0400-0500-0006-000700080009. I've not been able to garner info from web searches as to why this UUID could be blacklisted or how ZFS determines from which system the pool was last used.

Am I correct in my thinking that this is how ZFS 'thinks' the pool was last used by a foreign system?

Why are some UUIDs blacklisted?

Are motherboard UUIDs user editable or are they burned in?

What is the 'correct' way around this issue? It seems a bit wrong to force the import from rc.local on reboot.

I hope this makes sense. Thanks for any advice.
