I have what seems to be a contradiction about available space in my ZFS filesystem/pool. Basically, the zfs and zpool commands don't agree. I am hoping you can clear my confusion.
[For your listeners, since it's easier to read this description] I have 6 units of 8TB magnetic drives, arranged in 2x RAIDZ1 configuration. That is, my VDDVs are raidz1-0 and raidz1-1, which each VDEV consisting of 3 magnetic drives, 8 TB each drive.
[For your understanding, since it's easier to show in table format] 

Here is what it looks like in zpool status:
```
server% zpool status tank
  pool: tank
 state: ONLINE
  scan: scrub repaired 0 in 1 days 01:35:02 with 0 errors on Sun Mar  1 02:05:38 2020
config:
        NAME                      STATE     READ WRITE CKSUM
        tank                      ONLINE       0     0     0
          raidz1-0                ONLINE       0     0     0
            gpt/WDC-SATA-8TB-A    ONLINE       0     0     0
            gpt/SGT-SATA-8TB-A    ONLINE       0     0     0
            gpt/HGST-SATA-8TB-A   ONLINE       0     0     0
          raidz1-2                ONLINE       0     0     0
            gpt/WDC-SATA-8TB-B    ONLINE       0     0     0
            gpt/WDred-SATA-8TB-A  ONLINE       0     0     0
            gpt/WDC-SATA-8TB-C    ONLINE       0     0     0
        logs
          gpt/HP-EX900-A-zlog     ONLINE       0     0     0
        cache
          gpt/HP-EX920-A-cache    ONLINE       0     0     0
errors: No known data errors
```

If I do a zpool list, it shows:

```
server% zpool list tank
NAME   SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
tank  43.2T  40.1T  3.12T        -         -    31%    92%  1.00x  ONLINE  -
```

This shows 3.12 TB free. Since I added the 2nd set of 8TB drives later, this pool is not balanced. There are 444 GB free on the first VDEV but 2.69 TB free on the 2nd VDEV:

```
server% zpool list -v tank
NAME                       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
tank                      43.2T  40.1T  3.12T        -         -    31%    92%  1.00x  ONLINE  -
  raidz1                  21.6T  21.2T   444G        -         -    49%    97%
    gpt/WDC-SATA-8TB-A        -      -      -        -         -      -      -
    gpt/SGT-SATA-8TB-A        -      -      -        -         -      -      -
    gpt/HGST-SATA-8TB-A       -      -      -        -         -      -      -
  raidz1                  21.6T  18.9T  2.69T        -         -    13%    87%
    gpt/WDC-SATA-8TB-B        -      -      -        -         -      -      -
    gpt/WDred-SATA-8TB-A      -      -      -        -         -      -      -
    gpt/WDC-SATA-8TB-C        -      -      -        -         -      -      -
log                           -      -      -         -      -      -
  gpt/HP-EX900-A-zlog     63.5G  1.78M  63.5G        -         -     0%     0%
cache                         -      -      -         -      -      -
  gpt/HP-EX920-A-cache     256G   248G  8.04G        -         -     0%    96%
```

What confuses me, though, is that I would expect to see something like 2 TB free in ZFS: 3TB of raw space available, but reduced to 2 TB due to the RAIDZ1 parity. However, I only see 510 GB available:

```
server% zfs list tank
NAME   USED  AVAIL  REFER  MOUNTPOINT
tank  27.4T   510G   186K  /tank
```

I'm not sure if it matters, but I recently removed some old TV shows from my Plex DVR (and then destroyed the snapshots of the tank/PlexDVR file system). 

I'm a big confused, because the 510 GB does not make sense. It is not as much as I expected (2/3rds the sum of the individual VDEV's disk space), but is also more than the 444 GB on the individual VDEV (where I may have just freed up disk space).

In case it matters, here are the parameters in the filesystem:

```
server% zfs get all tank
NAME  PROPERTY                VALUE                   SOURCE
tank  type                    filesystem              -
tank  creation                Mon Nov  6 20:22 2017   -
tank  used                    27.4T                   -
tank  available               510G                    -
tank  referenced              186K                    -
tank  compressratio           1.00x                   -
tank  mounted                 yes                     -
tank  quota                   none                    default
tank  reservation             none                    default
tank  recordsize              128K                    default
tank  mountpoint              /tank                   default
tank  sharenfs                off                     default
tank  checksum                on                      default
tank  compression             off                     default
tank  atime                   on                      default
tank  devices                 on                      default
tank  exec                    on                      default
tank  setuid                  on                      default
tank  readonly                off                     default
tank  jailed                  off                     default
tank  snapdir                 hidden                  default
tank  aclmode                 discard                 default
tank  aclinherit              restricted              default
tank  createtxg               1                       -
tank  canmount                on                      default
tank  xattr                   off                     temporary
tank  copies                  1                       default
tank  version                 5                       -
tank  utf8only                off                     -
tank  normalization           none                    -
tank  casesensitivity         sensitive               -
tank  vscan                   off                     default
tank  nbmand                  off                     default
tank  sharesmb                off                     default
tank  refquota                none                    default
tank  refreservation          none                    default
tank  guid                    6139892547503978183     -
tank  primarycache            all                     default
tank  secondarycache          all                     default
tank  usedbysnapshots         234K                    -
tank  usedbydataset           186K                    -
tank  usedbychildren          27.4T                   -
tank  usedbyrefreservation    0                       -
tank  logbias                 latency                 default
tank  dedup                   off                     default
tank  mlslabel                                        -
tank  sync                    standard                default
tank  dnodesize               legacy                  default
tank  refcompressratio        1.00x                   -
tank  written                 74.6K                   -
tank  logicalused             26.7T                   -
tank  logicalreferenced       50.5K                   -
tank  volmode                 default                 default
tank  filesystem_limit        none                    default
tank  snapshot_limit          none                    default
tank  filesystem_count        none                    default
tank  snapshot_count          none                    default
tank  redundant_metadata      all                     default
tank  org.freebsd.ioc:active  yes                     local
```

And the same for the zpool:

```
server% zpool get all tank
NAME  PROPERTY                       VALUE                          SOURCE
tank  size                           43.2T                          -
tank  capacity                       92%                            -
tank  altroot                        -                              default
tank  health                         ONLINE                         -
tank  guid                           14783805901274647668           default
tank  version                        -                              default
tank  bootfs                         -                              default
tank  delegation                     on                             default
tank  autoreplace                    off                            default
tank  cachefile                      -                              default
tank  failmode                       wait                           default
tank  listsnapshots                  off                            default
tank  autoexpand                     off                            default
tank  dedupditto                     0                              default
tank  dedupratio                     1.00x                          -
tank  free                           3.12T                          -
tank  allocated                      40.1T                          -
tank  readonly                       off                            -
tank  comment                        -                              default
tank  expandsize                     -                              -
tank  freeing                        0                              default
tank  fragmentation                  31%                            -
tank  leaked                         0                              default
tank  bootsize                       -                              default
tank  checkpoint                     -                              -
tank  feature@async_destroy          enabled                        local
tank  feature@empty_bpobj            active                         local
tank  feature@lz4_compress           active                         local
tank  feature@multi_vdev_crash_dump  enabled                        local
tank  feature@spacemap_histogram     active                         local
tank  feature@enabled_txg            active                         local
tank  feature@hole_birth             active                         local
tank  feature@extensible_dataset     enabled                        local
tank  feature@embedded_data          active                         local
tank  feature@bookmarks              enabled                        local
tank  feature@filesystem_limits      enabled                        local
tank  feature@large_blocks           enabled                        local
tank  feature@large_dnode            enabled                        local
tank  feature@sha512                 enabled                        local
tank  feature@skein                  enabled                        local
tank  feature@device_removal         enabled                        local
tank  feature@obsolete_counts        enabled                        local
tank  feature@zpool_checkpoint       enabled                        local
tank  feature@spacemap_v2            active                         local
```