Hi Allan, Benedict and JT,

Thank you very much for your entertaining and informative podcast. If you don’t mind I’d like to ask you a a very unusual question. It’s about ZFS 😃.
Specifically about new compression algorithm Zstandard.

A) On my back up server all data sets are configured with ashift=12 (modern HDDs), compression=gzip-9 and recordsize=1M. Performance is bad but the only thing I care on the backup server is to store maximum amount of data. Could you please tell me does maximum level (19) of Zstandard apply better compression?

B) On my laptop and application server I use ashift=12 for HDDs and 13 for Samsung SSDs, compression=lz4 and minimum recordsize=16k or higher based on type of data. Based on my understanding lz4 is good even for laptop with weak CPUs because the bottleneck is usually storage and not CPU. Would you recommend replacing LZ4 by Zstandard both on laptop and server? Maybe higher level on XEON server and lower level on Intel i5 laptop?

Btw. I use encryption and skein checksums on both laptop, server and backup server but I don’t think that changes anything.

all my configs:
~~~
system: Debian 10 (laptop and server)
~~~
~~~
ashift     = 12  / 13 for SSDs
autotrim   = off / on for SSDs
delegation = on
~~~
~~~
atime         = off
checksum      = skein
compression   = lz4 / gzip-9 for backups
encryption    = aes-256-gcm
  keyformat   = raw
  keylocation = file:///bla/bla
recordsize    = 16k-1M / 1M for backups
xattr         = sa   (Linux recommendation)
  dnodesize   = auto (Linux recommendation)
~~~

Thank you very much for your excellent podcast and JT thumbs up for having blade servers at home 👍.

Kind regards
