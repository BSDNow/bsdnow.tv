Hey guys,

This will probably (hopefully) be a pretty easy one for FreeBSD old hats.

A couple of years ago, i upgraded two of the drives on my desktop system from 1TB drives to 3TB drives. So my system has 2 1TB WD blue SSDs in a mirrored pair, and 2 3TB spinning rust drives (a Hitachi and a Toshiba) also in a mirrored pair. Well, somewhere along the line in my zeal to get them configured and the system back up, I apparently failed to partition them. I noticed this because I made my system dual boot, and one time when booting back in to FreeBSD, I saw the following messages:

ada3: the primary GPT table is corrupt or invalid.
ada3: using the secondary instead -- recovery strongly advised.
ada4: the primary GPT table is corrupt or invalid.
ada4: using the secondary instead -- recovery strongly advised.

So my questions are, first, is it possible to properly partition these two drives, preferably without killing the contents of the drive? And second, how?

Thanks,
--b
