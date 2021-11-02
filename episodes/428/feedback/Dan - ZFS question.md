
We recently replaced one disk at a time to grow our six-disk ZFS array, resilvering every time.

Now, we get a report that there's a native block size mismatch, thusly:

  pool: z2
 state: ONLINE
status: One or more devices are configured to use a non-native block size.
    	Expect reduced performance.
action: Replace affected devices with devices that support the
    	configured block size, or migrate data to a properly configured
    	pool.
  scan: resilvered 5.59T in 1 days 05:21:10 with 0 errors on Sat May 11 04:15:26 2019
config:

    	NAME        	STATE 	READ WRITE CKSUM
    	z2          	ONLINE   	0 	0 	0
      	raidz2-0  	ONLINE   	0 	0 	0
        	gpt/disk12  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native
        	gpt/disk13  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native
        	gpt/disk14  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native
        	gpt/disk15  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native
        	gpt/disk16  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native
        	gpt/disk17  ONLINE   	0 	0 	0  block size: 512B configured, 4096B native

(For reference, here's the other pool with the original disks)

    	NAME        	STATE 	READ WRITE CKSUM
    	z1          	ONLINE   	0 	0 	0
      	raidz2-0  	ONLINE   	0 	0 	0
        	gpt/disk00  ONLINE   	0 	0 	0
        	gpt/disk01  ONLINE   	0 	0 	0
        	gpt/disk02  ONLINE   	0 	0 	0
        	gpt/disk03  ONLINE   	0 	0 	0
        	gpt/disk04  ONLINE   	0 	0 	0
        	gpt/disk05  ONLINE   	0 	0 	0

Is there a way to systematically resilver the array one disk at a time so I don't have to move EVERYTHING OFF and rebuild the array from scratch?

Apologies if this was covered on a previous podcast.  There are kinda a lot of them and they're not searchable as far as I can tell.

-Dan






















