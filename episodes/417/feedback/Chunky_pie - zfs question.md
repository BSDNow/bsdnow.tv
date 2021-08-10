Benedict and Allan,

Although I am an exclusive Linux user (I have yet to delve into BSD) I LOVE your show and above all the podcasts I listen to (the rest are Linux content based) non can compare to the technical knowledge your podcast delivers, thank you!

I have ZFS on my host machine and used Libvirt to create a libvirt storage pool and a volume (backed by ZFS) that I used as a disk on my Samba VM.  That virtual disk is then used to provide a samba share on my network. 


My problem is, that zvol has consumed all the space on the physical ZFS host disks so I added another vdev to the ZFS Pool, however that additional space is not reflected on the libvirt volume.  My research has indicated that I need to grow that volume however when I try:


     virsh vol-resize <volume> <storage pool>


I receive the following error - "error: this function is not supported by the connection driver: storage pool does not support changing of volume capacity"


My Questions:  How I can get the existing libvirt volume (zvol) to reflect the new capacity on the ZFS pool?  Am I SOL and have to just re-create the libvirt storage pool and volume with the new size of my available ZFS capacity?  Was there a better way to create a libvirt volume backed by my ZFS pool that would allow me to grow that libvirt volume as I add more disks to ZFS?

As always, eternally grateful.


Chunky_Pie
