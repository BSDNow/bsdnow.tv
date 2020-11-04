First of all Thanks for your show's. I like the style of the show
over
all my regular Linux podcast 

Way because. The “to the point” content of your shows is awesome!
The story of Netflix and  there encryption and the depth down to
the
hardware level, a while back..The depth this show can go into and I
still can follow along .Awesome!

My story and question;
I am running Suse lets say for 15 years on a home lab (which grow
from
a pIII,666mhz Vsftp-server nx-server,to 3 machines. First one main-
online, second one manual fail over, third one weekly backup. i
also
have a dell tl4000 tape drive for backups, a left over from my old
boss. I am Running Kvm/qemu Hypervisor running opnsense, ±15
docker
container like ldap tftp and nextcloud and a lot more.
For a year or 2 now, i use zfsonlinux, I am also running
4  raspberry
pi’s (all running Raspbian) true nfs/pxe boot without sd-card. I
now
have 4 raspberry*.img files mounted true a loop device whit
losetup..etc

[SEE SCRIPT](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/376/feedback/script.md)

The Question:.
  I see some fluctuating latency over my loop devices, whoud it be
a
better idea to switch from a *.img file to a zfs-dataset setup…?
Like
zfs create:

Raid10_pool/var/arm-images/raspi1
  copy the contend for x.img to Raid10_pool/var/arm-images/raspi1/.

whit additional options like quota, nfs exports etc?

  what would you 2 pros advise for running 4 pi’s and more in the
future, Image based or zfs-datasets, image are easy to copy to sd-
card
Aldo I never use those  should the zfs approach be faster ???

Second question
  are there any plans for the new compresion in zfs

grts form Holland
Thierry Reijnhout.
