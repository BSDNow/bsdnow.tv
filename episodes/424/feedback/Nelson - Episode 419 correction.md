Episode 419 reports that Debian dropped support for the DEC Alpha
at Debian 5.  That is no longer true: I have Debian 11 VMs running
on QEMU for Alpha, ARM664, HPPA, M68K, SPARC64, and S390x, and
Debian 10 for PowerPC (little-endian), CentOS 7 for PowerPC (big-endian),
CentOS 8 for PowerPC (little-endian).  For Debian 11 Alpha,  /proc/cpu
reports

cpu                     : Alpha
cpu model               : EV67
cpu variation           : 0
cpu revision            : 0
cpu serial number       : 
system type             : Tsunami
system variation        : Clipper

and lscpu says

Architecture:                    alpha
CPU op-mode(s):                  64-bit
Byte Order:                      Little Endian
CPU(s):                          1
On-line CPU(s) list:             0
Thread(s) per core:              1
Core(s) per socket:              1
Socket(s):                       1
Model:                           EV67
Model name:                      Alpha
BogoMIPS:                        518.32
...

I also have VMs for FreeBSD on ARM64 and RISC-V64, and many more.
