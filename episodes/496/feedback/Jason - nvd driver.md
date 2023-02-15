Hi everyone!  First, I've been a listener for years now -- truly a beneficial podcast to have out there!  Thanks for all that you put into the show!  One suggestion I had is to not read articles in their entirety.  I'd find more value in highlighting the article, pulling out key pieces of information, and directing people to the BSD Now website/article for more details.  I find listening to someone reading an article a bit much (for me).

My question:
I've been using the NVD driver for my NVMe drives (Samsung 980) for over a year now (since I built the machine), and it's mostly been working fine.  I've read about the NDA driver and wanted to try it to see if it was more performant, etc.  I switch to using it (by adding "hw.nvme.use_nvd=0" to /boot/loader.conf), and it rebooted fine and is now using the NDA driver.  However, now `zpool status` is showing:

--------
 pool: zroot
 state: ONLINE
status: One or more devices are configured to use a non-native block size.
	Expect reduced performance.
action: Replace affected devices with devices that support the
	configured block size, or migrate data to a properly configured
	pool.
  scan: scrub repaired 0B in 00:05:11 with 0 errors on Sun Jan 22 00:20:11 2023
config:

	NAME        STATE     READ WRITE CKSUM
	zroot       ONLINE       0     0     0
	  mirror-0  ONLINE       0     0     0
	    nda0p4  ONLINE       0     0     0  block size: 4096B configured, 16384B native
	    nda1p4  ONLINE       0     0     0  block size: 4096B configured, 16384B native

errors: No known data errors
--------

I've been using NVD for a long time without this error/warning -- why did switching to the NDA driver cause this, and better yet, how can I fix it and still use NDA (other than ignoring the warning)?  The drives are 4k sector drives (and is what the pool is using), so I'm not sure why ZFS is reporting that they're 16k sector drives instead.

Thanks for a great show!
