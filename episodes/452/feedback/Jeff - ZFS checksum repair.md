
Hi BSDNOW Team,

As always, I very much appreciate the work that you do in bringing us great BSD-focused content every week. I know you have said recently that you are running low on "feedback & questions" material, and I just so happen to have a timely problem to ask you about.

A couple of years ago, I bought a SuperMicro motherboard with an integrated Intel Atom CPU to play around with, which eventually turned into my home NAS server, recently upgraded to FreeBSD 13.0-RELEASE. As one does with the projects that turn into production machines, I cobbled together the remainder of the hardware (with the exception of the Seagate hard drives I'm using for data storage) with spare parts I had laying around. That included the RAM, which decided to finally give up the ghost last night some time after my weekly scrub started, causing the host to crash, and I awoke this morning to angry BIOS POST beeps. 

After finding a suitable replacement for the dead RAM amongst other spare parts, I was back up and running, and the scrub resumed. I noticed a short time later that the scrub had found checksum errors. Based on the following output, I believe the errors were successfully recovered:

====================================================================
 # zpool status
  pool: data
 state: ONLINE
status: One or more devices has experienced an unrecoverable error.  An
        attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
        using 'zpool clear' or replace the device with 'zpool replace'.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P
  scan: scrub repaired 1.88M in 19:56:41 with 0 errors on Sun Mar 27 20:57:41 2022
config:

        NAME                   STATE     READ WRITE CKSUM
        data                   ONLINE       0     0     0
          mirror-0             ONLINE       0     0     0
            gpt/zfs0-ZL20D1YS  ONLINE       0     0     5
            gpt/zfs1-ZL20B0T9  ONLINE       0     0    10
====================================================================

Have I interpreted the output correctly (that the errors were repaired)? Assuming so, this is of course a credit to the resilience of ZFS. But naturally, all of the data that can't be replaced is backed up with tarsnap :)

One additional question that I think is related: The RAM was pulled from one of my previous desktop PCs, and therefore was plain, consumer-grade RAM. Could ECC RAM have possibly prevented the checksum errors seen here? In other words, would ECC have prevented the corrupt data from being written to disk in the moments before failure? I monitor the daily zpool output messages, and as of the previous week's scrub there were no errors to speak of. I don't think the RAM would have failed as silently, in any case, as I would expect to see ECC errors in the system log. As it stands, there were no entries in /var/log/messages for approximately two days prior to my resurrecting the server on the new RAM this afternoon. If ZFS data corruption due to memory errors is a problem that ECC could help mitigate, it would give me a little extra incentive to upgrade.

Your opinions and expertise are always greatly appreciated, and hopefully I was able to help fill a little airtime.

Thanks,
Jeff











