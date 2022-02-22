Greetings and thank you for the great shows! I have what might be a dumb question.. I run pfsense and Truenas and use flavors of BSD/Unix/Solaris for work at Xerox. But I am by no means any sort of expert. On my Truenas server I pretty much just use it for storage and running a Plex server. I also have ran and plan to again run a Nextcloud server on it, it crashed when I was out of town and I have not fixed it yet... My question is should I be able to run VMs on this as well? 

I tried to get them to work but from what I could tell FreeBSD seemed to think I had to old hardware. This on an older dell server with Xeon processors. I run linux on another box that is identical and runs VMs on it as well as a proxmox server on this same hardware with no issues. I now realize while typing this that I probably should be giving much better details on the errors I ran into... I don't use this anywhere close to its capacity so that is why I was thinking of running VMs on it. Should this hardware with Truenas or if I load FreeBSD or another version of BSD on it be able to run VMs? Thank you again.

Intel(R) Xeon(R) CPU E5530 @ 2.40GHz.
Memory 23.9GiB total available (ECC) (I can add more memory and plan to double this amount).
TrueNAS-12.0-U7
12.2-Release-p11

Too much info....
FreeBSD 12.2-RELEASE-p11 75566f060d4(HEAD) TRUENAS amd64
FreeBSD clang version 10.0.1 (git@github.com:llvm/llvm-project.git llvmorg-10.0.1-0-gef32c611aa2)
VT(vga): text 80x25
CPU: Intel(R) Xeon(R) CPU           E5530  @ 2.40GHz (2394.05-MHz K8-class CPU)
  Origin="GenuineIntel"  Id=0x106a5  Family=0x6  Model=0x1a  Stepping=5
  Features=0xbfebfbff<FPU,VME,DE,PSE,TSC,MSR,PAE,MCE,CX8,APIC,SEP,MTRR,PGE,MCA,CMOV,PAT,PSE36,CLFLUSH,DTS,ACPI,MMX,FXSR,SSE,SSE2,SS,HTT,TM,PBE>
  Features2=0x9ce3bd<SSE3,DTES64,MON,DS_CPL,VMX,EST,TM2,SSSE3,CX16,xTPR,PDCM,DCA,SSE4.1,SSE4.2,POPCNT>
  AMD Features=0x28100800<SYSCALL,NX,RDTSCP,LM>
  AMD Features2=0x1<LAHF>
  VT-x: PAT,HLT,MTF,PAUSE,EPT,VPID
  TSC: P-state invariant, performance statistics
real memory  = 25769803776 (24576 MB)
avail memory = 24776372224 (23628 MB)
Event timer "LAPIC" quality 100
ACPI APIC Table: <DELL   PE_SC3  >
FreeBSD/SMP: Multiprocessor System Detected: 16 CPUs
FreeBSD/SMP: 2 package(s) x 4 core(s) x 2 hardware threads
random: unblocking device.
ioapic1: MADT APIC ID 1 != hw id 0
ioapic0 <Version 2.0> irqs 0-23 on motherboard
ioapic1 <Version 2.0> irqs 32-55 on motherboard
Launching APs: 1 7 3 11 5 13 15 2 6 14 9 10 4 12 8
Timecounter "TSC-low" frequency 1197023306 Hz quality 1000
random: entropy device external interface
kbd1 at kbdmux0
mlx5en: Mellanox Ethernet driver 3.5.2 (September 2019)
nexus0
vtvga0: <VT VGA driver> on motherboard
aesni0: No AES or SHA support.
padlock0: No ACE support.
cryptosoft0: <software crypto> on motherboard
acpi0: <DELL PE_SC3> on motherboard
acpi0: Power Button (fixed)
apei0: <ACPI Platform Error Interface> on acpi0
ipmi0: <IPMI System Interface> port 0xca8,0xcac on acpi0
ipmi0: KCS mode found at io 0xca8 on acpi
cpu0: <ACPI CPU> on acpi0
atrtc0: <AT realtime clock> port 0x70-0x7f irq 8 on acpi0
atrtc0: registered as a time-of-day clock, resolution 1.000000s
Event timer "RTC" frequency 32768 Hz quality 0
attimer0: <AT timer> port 0x40-0x5f irq 0 on acpi0
Timecounter "i8254" frequency 1193182 Hz quality 0
Event timer "i8254" frequency 1193182 Hz quality 100
hpet0: <High Precision Event Timer> iomem 0xfed00000-0xfed003ff on acpi0
Timecounter "HPET" frequency 14318180 Hz quality 950
Event timer "HPET" frequency 14318180 Hz quality 350
Event timer "HPET1" frequency 14318180 Hz quality 340
Event timer "HPET2" frequency 14318180 Hz quality 340
Event timer "HPET3" frequency 14318180 Hz quality 340
Timecounter "ACPI-fast" frequency 3579545 Hz quality 900
acpi_timer0: <24-bit timer at 3.579545MHz> port 0x808-0x80b on acpi0
pcib0: <ACPI Host-PCI bridge> port 0xcf8-0xcff on acpi0
pci0: <ACPI PCI bus> on pcib0
pcib1: <ACPI PCI-PCI bridge> at device 1.0 on pci0
pci1: <ACPI PCI bus> on pcib1
bce0: <QLogic NetXtreme II BCM5709 1000Base-T (C0)> mem 0xda000000-0xdbffffff irq 36 at device 0.0 on pci1
miibus0: <MII bus> on bce0
brgphy0: <BCM5709 10/100/1000baseT PHY> PHY 1 on miibus0
brgphy0:  10baseT, 10baseT-FDX, 100baseTX, 100baseTX-FDX, 1000baseT, 1000baseT-master, 1000baseT-FDX, 1000baseT-FDX-master, auto, auto-flow
bce0: Using defaults for TSO: 65518/35/2048
bce0: Ethernet address: a4:ba:db:21:ef:87
bce0: ASIC (0x57092003); Rev (C0); 
bce0: link state changed to DOWN
Bus (PCIe x4, 2.5Gbps); B/C (5.0.11); Bufs (RX:2;TX:2;PG:8); Flags (SPLT|MSI|MFW); MFW (NCSI 2.0.5)
Coal (RX:6,6,18,18; TX:20,20,80,80)
bce1: <QLogic NetXtreme II BCM5709 1000Base-T (C0)> mem 0xdc000000-0xddffffff irq 48 at device 0.1 on pci1
miibus1: <MII bus> on bce1
brgphy1: <BCM5709 10/100/1000baseT PHY> PHY 1 on miibus1
brgphy1:  10baseT, 10baseT-FDX, 100baseTX, 100baseTX-FDX, 1000baseT, 1000baseT-master, 1000baseT-FDX, 1000baseT-FDX-master, auto, auto-flow
bce1: Using defaults for TSO: 65518/35/2048
bce1: Ethernet address: a4:ba:db:21:ef:89
bce1: 
bce1: link state changed to DOWN
ASIC (0x57092003); Rev (C0); Bus (PCIe x4, 2.5Gbps); B/C (5.0.11); Bufs (RX:2;TX:2;PG:8); Flags (SPLT|MSI|MFW); MFW (NCSI 2.0.5)
Coal (RX:6,6,18,18; TX:20,20,80,80)
pcib2: <ACPI PCI-PCI bridge> at device 3.0 on pci0
pci2: <ACPI PCI bus> on pcib2
pcib3: <ACPI PCI-PCI bridge> at device 4.0 on pci0
pci3: <ACPI PCI bus> on pcib3
vgapci0: <VGA-compatible display> port 0xec00-0xecff mem 0xc0000000-0xcfffffff,0xdf1e0000-0xdf1fffff irq 33 at device 0.0 on pci3
pci3: <multimedia, HDA> at device 0.1 (no driver attached)
pcib4: <ACPI PCI-PCI bridge> at device 5.0 on pci0
pci4: <ACPI PCI bus> on pcib4
pcib5: <ACPI PCI-PCI bridge> at device 7.0 on pci0
pci5: <ACPI PCI bus> on pcib5
pcib6: <ACPI PCI-PCI bridge> at device 9.0 on pci0
pci6: <ACPI PCI bus> on pcib6
pcib7: <ACPI PCI-PCI bridge> at device 10.0 on pci0
pci7: <ACPI PCI bus> on pcib7
mpt0: <LSILogic SAS/SATA Adapter> port 0xfc00-0xfcff mem 0xdf3ec000-0xdf3effff,0xdf3f0000-0xdf3fffff irq 41 at device 0.0 on pci7
mpt0: MPI Version=1.5.18.0
mpt0: Capabilities: ( RAID-0 RAID-1E RAID-1 )
mpt0: 0 Active Volumes (2 Max)
mpt0: 0 Hidden Drive Members (14 Max)
pci0: <base peripheral, interrupt controller> at device 20.0 (no driver attached)
pci0: <base peripheral, interrupt controller> at device 20.1 (no driver attached)
pci0: <base peripheral, interrupt controller> at device 20.2 (no driver attached)
uhci0: <Intel 82801I (ICH9) USB controller> port 0xdc40-0xdc5f irq 17 at device 26.0 on pci0
usbus0 on uhci0
usbus0: 12Mbps Full Speed USB v1.0
uhci1: <Intel 82801I (ICH9) USB controller> port 0xdc60-0xdc7f irq 18 at device 26.1 on pci0
usbus1 on uhci1
usbus1: 12Mbps Full Speed USB v1.0
ehci0: <Intel 82801I (ICH9) USB 2.0 controller> mem 0xdf0fe000-0xdf0fe3ff irq 19 at device 26.7 on pci0
usbus2: EHCI version 1.0
usbus2 on ehci0
usbus2: 480Mbps High Speed USB v2.0
uhci2: <Intel 82801I (ICH9) USB controller> port 0xdc80-0xdc9f irq 21 at device 29.0 on pci0
usbus3 on uhci2
usbus3: 12Mbps Full Speed USB v1.0
uhci3: <Intel 82801I (ICH9) USB controller> port 0xdca0-0xdcbf irq 20 at device 29.1 on pci0
usbus4 on uhci3
usbus4: 12Mbps Full Speed USB v1.0
uhci4: <Intel 82801I (ICH9) USB controller> port 0xdcc0-0xdcdf irq 21 at device 29.2 on pci0
usbus5 on uhci4
usbus5: 12Mbps Full Speed USB v1.0
uhci5: <Intel 82801I (ICH9) USB controller> port 0xdce0-0xdcff irq 20 at device 29.3 on pci0
usbus6 on uhci5
usbus6: 12Mbps Full Speed USB v1.0
ehci1: <Intel 82801I (ICH9) USB 2.0 controller> mem 0xdf0ff000-0xdf0ff3ff irq 21 at device 29.7 on pci0
usbus7: EHCI version 1.0
usbus7 on ehci1
usbus7: 480Mbps High Speed USB v2.0
pcib8: <ACPI PCI-PCI bridge> at device 30.0 on pci0
pci8: <ACPI PCI bus> on pcib8
vgapci1: <VGA-compatible display> mem 0xd0000000-0xd07fffff,0xde7fc000-0xde7fffff,0xde800000-0xdeffffff irq 19 at device 3.0 on pci8

