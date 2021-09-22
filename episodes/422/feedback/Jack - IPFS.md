Dear Allan, Benedict, Tom and JT,

Thank you very much for your excellent show and for giving people opportunity to ask questions.

In episode 414 Tom and Benedict discussed article about IPFS. Is that something you have experience with?

For a long time I'm after self replicating open-source filesystem.

My needs are:
- File based, not block storage based (NAS, not SAN)
- Multiple hosts that are replicating files between each other with automatic failover
- It works as an abstraction on top of normal filesystem, in other words in case of failure you can recover files simply by copying them from ZFS, Ext4...
- Not some crazy complicated monstrosity like Ceph or Hadoop
- Access the storage via NFS or anything else that works and can be installed on Linux and BSD, Windows and MacOS support is not needed

I tried a few of filesystems like that but I always had some issues and reverted back to simply use ZFS and send snapshots between multiple hosts. GlusterFS is probably the best but what about IPFS? Is it possible to use it like this?

Thank you.

Best regards,

Jack
