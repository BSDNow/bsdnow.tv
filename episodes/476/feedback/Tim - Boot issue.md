Hey, BSDNow team,

A recent freebsd-update to 13.0-RELEASE-p11 prevented my systems
from booting.  Reinstalling the boot-code[1] resolved the issue on
my daily driver at home.

However, on my VPS, I don't have boot-to-install-media to run `gpart
bootcode`.  All I get is a Debian rescue environment[2].  Is there
a way to effectively get the same results as a `gpart bootcode`
using dd(1) on Linux if I can provide the bootcode files (/boot/pmbr
& /boot/gptzfsboot) to the Linux rescue environment?

Thanks,

-Tim

[1]
https://forums.freebsd.org/threads/10-1-doesnt-boot-anymore-from-zroot-after-applying-p25.54422/

[2] which is how I got the install there in the first place,
creating a disk-backed md device, running the installer against it,
and doing

 $ gzip -9 vps.img | ssh root@$RESCUEIP 'gunzip - | dd of=/dev/sd2'

Both systems were roughly the same disk layout when you do an install
choosing ZFS-on-GELI with no additional modifications.  Here's from
the local (fixed) laptop, but the VPS layout was created in the same
form

$ gpart list
Geom name: ada0
modified: false
state: OK
fwheads: 16
fwsectors: 63
last: 488397127
first: 40
entries: 128
scheme: GPT
Providers:
1. Name: ada0p1
   Mediasize: 524288 (512K)
   Sectorsize: 512
   Stripesize: 0
   Stripeoffset: 20480
   Mode: r0w0e0
   efimedia: HD(1,GPT,ea73cdb7-7bdf-11e9-8cbc-b870f41e1ef2,0x28,0x400)
   rawuuid: ea73cdb7-7bdf-11e9-8cbc-b870f41e1ef2
   rawtype: 83bd6b9d-7f41-11dc-be0b-001560b84f0f
   label: gptboot0
   length: 524288
   offset: 20480
   type: freebsd-boot
   index: 1
   end: 1063
   start: 40
2. Name: ada0p2
   Mediasize: 250058113024 (233G)
   Sectorsize: 512
   Stripesize: 0
   Stripeoffset: 1048576
   Mode: r1w1e1
   efimedia: HD(2,GPT,ea79d37e-7bdf-11e9-8cbc-b870f41e1ef2,0x800,0x1d1c5000)
   rawuuid: ea79d37e-7bdf-11e9-8cbc-b870f41e1ef2
   rawtype: 516e7cba-6ecf-11d6-8ff8-00022d09712b
   label: zfs0
   length: 250058113024
   offset: 1048576
   type: freebsd-zfs
   index: 2
   end: 488396799
   start: 2048
Consumers:
1. Name: ada0
   Mediasize: 250059350016 (233G)
   Sectorsize: 512
   Mode: r1w1e2

$ geli list
Geom name: ada0p2.eli
State: ACTIVE
EncryptionAlgorithm: AES-XTS
KeyLength: 256
Crypto: software
Version: 7
UsedKey: 0
Flags: BOOT, GELIBOOT
KeysAllocated: 59
KeysTotal: 59
Providers:
1. Name: ada0p2.eli
   Mediasize: 250058108928 (233G)
   Sectorsize: 4096
   Mode: r1w1e1
Consumers:
1. Name: ada0p2
   Mediasize: 250058113024 (233G)
   Sectorsize: 512
   Stripesize: 0
   Stripeoffset: 1048576
   Mode: r1w1e1

