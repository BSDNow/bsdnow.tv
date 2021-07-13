Hi Guys,

I have a ZFS on root system running FreeBSD.  I installed Lumina DE, including the file manager (Lumina-FM).  I have not been able to view snapshots via Lumina-FM, however. Apparently, there's supposed to be some type of "backup" button" that appear in the toolbar when you select a dataset that has snapshots, but I can't get it, nor the "timeline slider" or similar,  to appear.

I did some searching online, but only found some old PC-BSD forum posts, one if which had a solution of not using a soft link.  I confirmed that I am not using a soft link, but still no joy.

Any idea how I can get this functionality to appear would be greatly appreciated.

Thanks in advance,
Tim


### Producers Reply

You are correct, the Lumina File manager should be able to browse through past snapshots of the directory you are in.  I spoke with Ken about this and this is what we came up with.
1. Your dataset is not "readable" by the user (root only or some such thing for the base dataset dir)
2. You don't have the "snapdir" property setup correctly (so the hidden ".zfs/snapshot" dir is not browsable).
