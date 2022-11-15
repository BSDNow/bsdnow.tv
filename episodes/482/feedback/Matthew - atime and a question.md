Been a listener since the first episode, LOVE the show, please keep it up!

An episode or two ago the two of you were asking/debating the need/usefulness of keeping ATIME active, and "what's it still used or needed for?".

Shared files.  The NFS subsystem has excellent file-lock checks in place, but even with lower latency modern switches (Link Aggregation complicates this) it's still possible that 2 connections will compete for file access (and lock) first.  The ATIME attribute gives the final vote in who gets the file.
ComputerA & ComputerB both ask for File1 at the exact same time.
The ATIME value is sent back to both Computers.
The Computer that reports back the "oldest" ATIME (meaning they got the reply back first) wins the tie.

Now time for my question:
I have a FreeBSD ZFS file server that's been running for several years. Since 11.2-RELEASE if I remember correctly.  Since upgrading to 13.1-RELEASE my ZFS pool does not load automatically.
I need to manually run:   zpool import storage_pool
My boot drive is UFS.
ZFS pool is a simple raidz1.

config:

        NAME          STATE     READ WRITE CKSUM
        storage_pool  ONLINE       0     0     0
          raidz1-0    ONLINE       0     0     0
            ada0      ONLINE       0     0     0
            ada1      ONLINE       0     0     0
            ada2      ONLINE       0     0     0
            ada3      ONLINE       0     0     0
            ada4      ONLINE       0     0     0

errors: No known data errors

Any advice?
