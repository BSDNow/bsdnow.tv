
A technical question on the internals of ZFS.

ZFS is a C.O.W. or copy-on-write file system.

This implies every write to a file results in a new copy of the file. Some folks take this literally. I suspect ZFS is more efficient than this. Can someone with expertise confirm?

Here's an example.

A log file is created and one line of text written. That text appears on a disk block. The rest of the disk block is empty.

Later, a new line of text is written to the file.

So the question is ... does ZFS allocate a new block (containing both lines of text) or does ZFS append the data to the existing block? I suspect ZFS does not need to make a copy for append-only data. The block with the meta-data should be copied (because the file length changed) but the block with append only content can stay.

A rollback of the transaction need only update the file length. This is such low hanging fruit that I can't imagine ZFS not already doing this.

What do the ZFS experts have to say?

Regards,
Rick
