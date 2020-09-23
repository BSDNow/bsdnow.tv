First off, thanks for an awesome show! I've been a listener for several years now and have learned a lot from you all. Keep up the great work.

I recently installed FreeBSD (13.0-CURRENT) on my Lenovo Yoga 720-13IKB to give it another test drive. I ran into trackpad issues in the past, but I noticed there is a generic HID layer project that looked promising.

Resource: https://github.com/wulf7/iichid: Generic HID layer for FreeBSD. Including I2C and USB backends.

After a quick install and a reboot, I was pleasantly surprised to have a working trackpad. Everything else worked, but wifi was dreadfully slow.  It occurred to me that bhyve might offer a solution. I could passthru the wifi card to a Linux distro and use the Linux driver to push the device. Then, I could do some simple networking to route my FreeBSD host traffic through that virtual machine. As it turns out, that works quite well. Here’s a quick run through of the steps I followed.

The first step is to disconnect the wifi card (PCI device) from the host to allow the VM to drive it.

# pciconf -l -v
...
iwm0@pci0:63:0:0:	class=0x028000 rev=0x78 hdr=0x00 vendor=0x8086 device=0x24fd subvendor=0x8086 subdevice=0x1010
    vendor     = 'Intel Corporation'
    device     = 'Wireless 8265 / 8275'
    class      = network

Add this line to the /boot/loader.conf, and reboot.
pptdevs="63/0/0"

After reboot, verify that the device is no longer available to the host. It should be listed as a ppt device now.

# pciconf -l -v 
ppt0@pci0:63:0:0:	class=0x028000 rev=0x78 hdr=0x00 vendor=0x8086 device=0x24fd subvendor=0x8086 subdevice=0x1010
    vendor     = 'Intel Corporation'
    device     = 'Wireless 8265 / 8275'
    class      = network

The next steps are to create a bhyve VM. There are tons of “how-to” resources on this, but decided to stick with the Handbook (https://www.freebsd.org/doc/handbook/virtualization-host-bhyve.html)

Step 1: download the Linux iso (I chose Debian 10)

Step 2: create an .img file (or you could use a zfs volume).

Step 3: create a .map file to point to the .img and .iso files

# debian.map
(hd0) ./debian10.img
(cd0) ./debian10.iso

Step 4: use grub-bhyve to load the kernel, allocate memory, and devices. Please note the -S in the post installation command. This is to wire guest memory, which is required to access the ppt device.

First boot, will be with cd0 for the installation.
grub-bhyve -m debian10.map -r cd0 -M 1024M debian10

Post installation, we’ll use the hd0 device.
grub-bhyve -S -m debian10.map -r hd0,msdos1 -M 1024M debian10

Step 5: boot the VM. On the first boot, Please note the -S again on the post installation command. Also, I dropped the -s 4:0,ahci-cd device on post installation.

bhyve -A -H -P -s 0:0,hostbridge -s 1:0,lpc -s 2:0,virtio-net,tap0 -s 3:0,virtio-blk,./debian10.img -s 4:0,ahci-cd,./debian10.iso -l com1,stdio -c 4 -m 1024M debian10

bhyve -A -H -P -S -s 0:0,hostbridge -s 1:0,lpc -s 2:0,virtio-net,tap0 -s 3:0,virtio-blk,./debian10.img -s 7:0,passthru,63/0/0 -l com1,stdio -c 4 -m 1024M debian10


Depending on the Linux distro you choose, the iwlwifi driver may be included in the .iso. Unfortunately, my selection of debian10 did not. So, I had to download the driver and get it installed in the VM. There are several ways to do this. I decided to just mount the .img file using mdconfig and copy the .deb file into it.

Resource: https://gist.github.com/yzgyyang/4965d5673b5c79c644a695dd75fa8e05: FreeBSD mount img files
 
After the firmware was installed, the wifi device was accessible within the VM. From there, I was able to configure it to connect to my wifi and enable the packet forwarding within the VM. Wow! What a difference…. I went from around 20Mbits/s to 250Mbits/s. Here is a quick iperf between my workstation and the laptop on the same network:

# using native iwm driver
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  2.88 MBytes  24.1 Mbits/sec
[  3]  1.0- 2.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  2.0- 3.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  3.0- 4.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3]  4.0- 5.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  5.0- 6.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3]  6.0- 7.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  7.0- 8.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  8.0- 9.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3]  9.0-10.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 10.0-11.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 11.0-12.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3] 12.0-13.0 sec  2.38 MBytes  19.9 Mbits/sec
[  3] 13.0-14.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 14.0-15.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 15.0-16.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3] 16.0-17.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 17.0-18.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 18.0-19.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3] 19.0-20.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 20.0-21.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 21.0-22.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 22.0-23.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 23.0-24.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 24.0-25.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3] 25.0-26.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 26.0-27.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 27.0-28.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3] 28.0-29.0 sec  2.62 MBytes  22.0 Mbits/sec
[  3] 29.0-30.0 sec  2.50 MBytes  21.0 Mbits/sec
[  3]  0.0-30.0 sec  77.8 MBytes  21.7 Mbits/sec


# routing through the bhyve VM
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  19.9 MBytes   167 Mbits/sec
[  3]  1.0- 2.0 sec  30.6 MBytes   257 Mbits/sec
[  3]  2.0- 3.0 sec  29.4 MBytes   246 Mbits/sec
[  3]  3.0- 4.0 sec  21.6 MBytes   181 Mbits/sec
[  3]  4.0- 5.0 sec  26.8 MBytes   224 Mbits/sec
[  3]  5.0- 6.0 sec  23.4 MBytes   196 Mbits/sec
[  3]  6.0- 7.0 sec  32.5 MBytes   273 Mbits/sec
[  3]  7.0- 8.0 sec  20.9 MBytes   175 Mbits/sec
[  3]  8.0- 9.0 sec  33.2 MBytes   279 Mbits/sec
[  3]  9.0-10.0 sec  38.4 MBytes   322 Mbits/sec
[  3] 10.0-11.0 sec  27.8 MBytes   233 Mbits/sec
[  3] 11.0-12.0 sec  29.2 MBytes   245 Mbits/sec
[  3] 12.0-13.0 sec  33.9 MBytes   284 Mbits/sec
[  3] 13.0-14.0 sec  28.4 MBytes   238 Mbits/sec
[  3] 14.0-15.0 sec  27.1 MBytes   228 Mbits/sec
[  3] 15.0-16.0 sec  25.9 MBytes   217 Mbits/sec
[  3] 16.0-17.0 sec  28.1 MBytes   236 Mbits/sec
[  3] 17.0-18.0 sec  32.4 MBytes   272 Mbits/sec
[  3] 18.0-19.0 sec  35.0 MBytes   294 Mbits/sec
[  3] 19.0-20.0 sec  36.8 MBytes   308 Mbits/sec
[  3] 20.0-21.0 sec  24.0 MBytes   201 Mbits/sec
[  3] 21.0-22.0 sec  25.8 MBytes   216 Mbits/sec
[  3] 22.0-23.0 sec  30.2 MBytes   254 Mbits/sec
[  3] 23.0-24.0 sec  37.8 MBytes   317 Mbits/sec
[  3] 24.0-25.0 sec  42.1 MBytes   353 Mbits/sec
[  3] 25.0-26.0 sec  30.8 MBytes   258 Mbits/sec
[  3] 26.0-27.0 sec  28.5 MBytes   239 Mbits/sec
[  3] 27.0-28.0 sec  33.6 MBytes   282 Mbits/sec
[  3] 28.0-29.0 sec  37.8 MBytes   317 Mbits/sec
[  3] 29.0-30.0 sec  42.0 MBytes   352 Mbits/sec
[  3]  0.0-30.0 sec   914 MBytes   255 Mbits/sec


Needless to say, I’m pretty happy with the results and wanted to share the concept with the community. While I would prefer the native iwm driver to deliver on the same bandwidth as the Linux version, this is an acceptable workaround for me.

Thanks
Chris