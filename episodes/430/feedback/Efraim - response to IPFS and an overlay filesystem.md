In response to Jack's email in episode 426 about having a
self-replicating file system on top of ZFS:

The quick answer I can think of is syncthing. Selective sync will keep
certain machines from trying to use more space than they have and
satisfies Jack's requirement to be able to copy raw files back if the
replication system fails.

In relation to the mention of LizardFS, I set up lizardfs on a small HPC
cluster at work (just 11 machines). My reasoning is that:
1. Not all machines have the same number of drives or of the same size
or add new drives at the same rate, so Ceph wasn't going to work for us.
2. The head node for the cluster is also the head node for the lizardfs
system. If the head node goes down we're not computing until it's back
up anyway, but our fallback scheduling node is also our fallback
lizardfs head node.
3. File access is available through the lizardfs mount point on each
local machine or through an NFS export/samba share. File reads isn't
slower than network access, although depending on your file replication
plan writes can be very fast or very slow.

It doesn't have the option of straight copying off files if the system
fails but it's been working great at work long enough that my wife is
willing to let me set it up at home too.
