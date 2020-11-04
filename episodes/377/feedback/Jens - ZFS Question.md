Hi,

at first greetings and thanks for this great podcast.
I've got a ZFS question regarding the removal of bootpool from FreeBSD 11 to 12.

At work I inherited a server running 12.1-RELEASE which was updated from 11 and there was trouble during the upgrade process due to the /boot directory gone missing. I examined it a bit and found that there are 2 ZFS pools: bootpool and zroot:

```
# zpool status
  pool: bootpool
  ...
config:

        NAME        STATE     READ WRITE CKSUM
        bootpool    ONLINE       0     0     0
          mirror-0  ONLINE       0     0     0                                                            
            da0p3   ONLINE       0     0     0
            da1p3   ONLINE       0     0     0                                                            
            da2p3   ONLINE       0     0     0
            da3p3   ONLINE       0     0     0                                                            

  pool: zroot
  ...
config:

        NAME           STATE     READ WRITE CKSUM
        zroot          ONLINE       0     0     0
          raidz2-0     ONLINE       0     0     0
            da0p5.eli  ONLINE       0     0     0
            da1p5.eli  ONLINE       0     0     0
            da2p5.eli  ONLINE       0     0     0
            da3p5.eli  ONLINE       0     0     0
# zfs list | grep boot
bootpool                                  185M  1,68G   180M  /bootpool
# ls -la /boot
lrwxr-xr-x  1 root  wheel  14  8 Nov.  2019 /boot -> /bootpool/boot
```

So the zroot pool is sitting on encrypted partitions and the bootpool not.
Finally we come to my question. 

Is it possible to remove the bootpool without breaking the system?
Maybe this would be an opportunity to look into beadm? 

Kind regards,

Jens