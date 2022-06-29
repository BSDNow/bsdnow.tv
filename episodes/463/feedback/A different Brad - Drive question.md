My two 3TB spinning rust drives were pulled out of my TrueNAS box when I upgraded to 4TB drives and put in my desktop system. These are data drives, a pool for large stuff that I don't want on my primary pool, which is mirrored pair of SSDs. So I stuck them in, and created the mirrored pair. But I just wrote the pool to the drives. So I get the messages below:

ada3: the primary GPT table is corrupt or invalid.
ada3: using the secondary instead -- recovery strongly advised.
ada4: the primary GPT table is corrupt or invalid.
ada4: using the secondary instead -- recovery strongly advised.

So I wanted to get a sanity check before I trash the pool...Here is what I have determined I need to do:

zpool detach NCC1764 /dev/ada3

gpart create -s gpt /dev/ada3
gpart add -t freebsd-swap -a 4K -s 2048M /dev/ada3
gpart add -t freebsd-zfs -a 4K /dev/ada3

zpool attach NCC1764 /dev/ada3

So at that point, I let the pool resilver, then lather/rinse/repeat with ada4. Does that sound reasonable?

Thanks man,
--b