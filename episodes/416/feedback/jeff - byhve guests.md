Hi Benedict, Alan and JT,

As usual, thanks for a great podcast. I listen every week. Your recent discussion of byhve and ZFS (Episode 375) prompted me with a question, as I have recently created a solution related to ZFS and bhyve in my own FreeBSD environment at home. 

I am using Ansible and vm-bhyve to reprovision bhyve FreeBSD guests, and before booting the new guest, I am setting the hostname and network information in rc.conf. The workflow goes like this:

    Destroy the old guest, if it exists.
    (Re-)create the guest from a stored VM image.
    Import the zroot pool from the guest disk image via mdconfig as a temporary pool called 'tmproot' on the VM host and mount the guest's zroot under /mnt/disk.
    Change the necessary information in the guest's rc.conf.
    Unmount the guest's disk and boot the VM.

This brings me to the point of my question: Using Google and mining the FreeBSD forums was quite sufficient to find the necessary information for mounting the guest disk image. What was less clear is the "right" way to unmount the guest zroot once I am done. Currently I am doing:

zfs unmount tmproot/ROOT/default  #to unmount the guest's zroot file system
zfs export tmproot  #to export the guest's zroot pool.
mdconfig -d -u 0  #to destroy the memory disk /dev/md0

Is there a better way to do this unmount/export procedure? Am I risking any damage to the guest's disk/ZFS file system by doing it the way that I am?

Thanks in advance and keep up the great work,
