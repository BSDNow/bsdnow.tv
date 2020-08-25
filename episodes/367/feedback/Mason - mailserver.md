I forget if there's another address for questions now, but this appears to
be the last one I used, so:

I'm migrating a mail server to a FreeBSD jail, and I've seen conflicting
notes about how best to tune ZFS for holding accounts with Maildirs. My
current thinking is that I don't want to change recordsize as it's an upper
limit, not a minimum, but that I might want to set primarycache=metadata so
I'm caching information about Maildir contents, but not the Maildir
contents themselves. But are these valid thoughts, and what else is there
to think about? The problem is that I don't know what I don't know, and I'm
not sure about what I do know, so I'd love some advise about how best to
tune a dataset for Maildirs.