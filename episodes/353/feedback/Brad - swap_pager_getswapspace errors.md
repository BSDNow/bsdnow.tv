Hello, Benedict, JT, and Allan,

I am running into an issue, and I am not sure if it is actually affecting performance on my FreeBSD 12.1-RELEASE box. I am running ZFS with a mirrored pair of 250GB SSDs as my primary pool, and a pair of 1TB spinning drives as the pool for all my big/thrashy stuff.

What I have noticed is that occasionally, my performance will get really bad, my graphics will get really choppy, and even though I appear, according to htop to be using 5.2GB of 16GB of RAM, my swap will be almost full:

  1  [|      0.4%]   4  [||     0.9%]   7  [||     2.6%]   10 [       0.0%]
  2  [|      0.4%]   5  [       0.0%]   8  [|      0.4%]   11 [       0.0%]
  3  [       0.0%]   6  [|      0.4%]   9  [|      0.4%]   12 [||     0.9%]
  Mem[|||||||||||||||||||5.21G/15.9G]   Tasks: 118, 0 thr; 2 running
  Swp[                      0K/4.00G]   Load average: 0.17 0.21 0.17
                                        Uptime: 01:11:46

Well, tonight when I rebooted, I saw a number of dmesg messages like:

swap_pager_getswapspace(18): failed
swap_pager_getswapspace(9): failed
swap_pager_getswapspace(3): failed
swap_pager_getswapspace(3): failed

I did some preliminary web searches, and found a bug report from 2009, and a  2018 mailing list thread. The latter talks about the ZFS arc cache. (and thus by magic, it turns into a ZFS question... :D )

Is this a ZFS problem? How do I determine it? Unfortunately, I just rebooted this evening, which is when I saw the swap_pager_getswapspace messages.

Thanks,
--b