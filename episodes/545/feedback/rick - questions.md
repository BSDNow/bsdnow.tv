

To Allan, Benedict, JT and the whole BSDNow team;

How does ZFS copy-on-write handle deleting large directories?
Example: my /usr/ports was out of date and 'git fetch' didn't work so I did an 'rm -rf /usr/ports' to remove it all (and later run 'git clone' to recreated /usr/ports). Near the end I started to see "device busy". My guess is ZFS was busy doing something in the background.

I suspect 'rm' recursively deletes all the leaf nodes first as it works its way up. This would give ZFS a ton of data to copy-on-write.

Would it be feasible for ZFS to treat the top level directory removal as a single transaction instead of hundreds or thousands of smaller transactions?

How does ZFS handle append-only transactions to a file?
If the last block of a file has enough room for the write operation, it seems to me ZFS need not create a new block with the original data plus the appended data. Instead, it need only record the new vs. old file length and append the data into the existing block. There's enough information to roll back the transaction without swapping the last block.

I can't read the ZFS source code well enough to determine if this is the case.

Love your show!

Regards, Rick






