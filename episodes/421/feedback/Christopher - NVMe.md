I’ve really enjoyed the ZFS filesystem.  I’ve listened and read a little about beadmin and bectl and they’re great ideas but they don’t do exactly what I want.

I use NVMe drives for the OS installs on all my machines and then I have one server that NFS exports 45TB of ZFS spinning rust which stores all my data and home directories.  These NVMe drives are big and cheap enough I can afford to have multiple OS installs and still have plenty of space.  When it comes time to install a new version of FreeBSD I’d like to essentially create a new ZFS filesystem and install to the new filesystem, from within the old running OS.  If I mount the new file system from within the old running OS I can configure it and install packages without bringing down the server.  Then a single reboot can switch over and I still have the old system for reference or to roll back to.  This is a lot like what beadmin/bectl does BUT, if I understand correctly, these setups install over a working snapshot.  I want to start with a completely clean system, so that viruses or old files that are no longer used and that don’t get overwritten by the install will not hang around.  I’d appreciate any feedback you have.  Can beadmin/bectl operate in this kind of mode?  If not can you outline briefly what I might do to achieve this myself?  The only system filesystem I might want share across versions is /tmp given this is there any really advantage to having things like /usr /var and the other separate filesystems that are generally created in a FreeBSD install?

Keep up the good work, I enjoy it.
Regards


 
