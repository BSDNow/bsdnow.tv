#!/bin/bash
#script to fresh install rasbian and kodi etc etc
SerialNR=127f9adf
rasbarrynr=1
loopdev="/dev/loop$rasbarrynr"
#clear

inputimage="/mnt/bigpart/repo/2019-07-10-raspbian-buster-lite.img"
outputimage="/mnt/arm-images/Running-raspbian-$SerialNR.img"
mountpoint="/mnt/arm-images/Raspi$rasbarrynr"

if [ "$1" = 1 ]
 then
 #fresh install!!!!!
 docker stop Tftp-server
 echo "$(grep -v $mountpoint /etc/exports)" > /etc/exports
 exportfs -ra
 umount "$loopdev"p1; umount "$loopdev"p2
 umount $mountpoint
 umount "/mnt/bigpart/Docker_files/Tftp-server/var_tftpboot/$SerialNR"
 losetup -d $loopdev
  sleep 3
  rm -r /mnt/bigpart/Docker_files/Tftp-server/var_tftpboot/$SerialNR
  mkdir /mnt/bigpart/Docker_files/Tftp-server/var_tftpboot/$SerialNR
  mkdir $mountpoint
  echo "fress Install coppying from: $inputimage to: $outputimage"
  cp -vf $inputimage $outputimage
  echo "enlarge disk space"
  dd if=/dev/zero bs=512b count=26215 >> $outputimage status=progress
  echo "resize partitions"
  parted $outputimage --script resize 2 100%
  #parted $outputimage -l
   #mount image to dedicated dir resize partition umount....
    losetup -P "$loopdev" $outputimage
    echo "filesystem check"
    sleep 2
    e2fsck -f "$loopdev"p2
    resize2fs "$loopdev"p2
    mkdir /tmp/bootdir
     mount -o rw "$loopdev"p1 /tmp/bootdir
      rsync -av /tmp/bootdir/* /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR/.
       chmod -R 777 /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR
     umount /tmp/bootdir
    rmdir -r /tmp/bootdir
    mount -o rw "$loopdev"p2 $mountpoint  
    #place the right preconfigured files on right location.
     touch /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR/ssh     #to activate sshd not tested
     #cp -f /mnt/bigpart/repo/postinstall/Raspbian/cmdline.txt
/mnt/bigpart/Docker_files/Tftp-server/var_tftpboot/$SerialNR/.
      rm /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR/cmdline.txt
      echo "dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1
root=/dev/nfs nfsroot=10.0.4.1:$mountpoint,tcp,vers=4 rw ip=dhcp
rootwait elevator=deadline modprobe.blacklist=bcm2835_v4l2"
>>  /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR/cmdline.txt
      echo "Raspi$rasbarrynr" > $mountpoint/etc/hostname
      cp -f /mnt/bigpart/repo/postinstall/Raspbian/fstab
$mountpoint/etc/.
       echo "10.0.4.1:/mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR  /boot           nfs    defaults,vers=3  
       0       0" >> $mountpoint/etc/fstab
       cp -f
/mnt/bigpart/repo/postinstall/Raspbian/config_raspi$rasbarrynr.txt
/mnt/bigpart/Docker_files/Tftp-server/var_tftpboot/$SerialNR/config.txt
       cp -f /mnt/bigpart/repo/postinstall/Raspbian/rc.local
$mountpoint/etc/rc.local
     rsync -av /mnt/bigpart/repo/postinstall/Raspbian/Root_home-
Raspi$rasbarrynr/* $mountpoint/root/.     #file rights not tested
     rsync -av /mnt/bigpart/repo/postinstall/Raspbian/Root_home-
Raspi$rasbarrynr/.ssh $mountpoint/root/.
    umount "$loopdev"p1
    umount "$loopdev"p2
     echo
"$mountpoint   *(rw,fsid=$rasbarrynr,no_subtree_check,async,no_root_squ
ash)" >> /etc/exports
  exportfs -ra   
 elif [ "$1" = 2 ]
  then
   #mount image to dedicated dir  (reboot server start)
    losetup -P "$loopdev" $outputimage
    echo "filesystem check"
    e2fsck -f "$loopdev"p2
    mount -o rw "$loopdev"p2 $mountpoint
    #mount -o rw "$loopdev"p1 /mnt/bigpart/Docker_files/Tftp-
server/var_tftpboot/$SerialNR 
     #sh /mnt/bigpart/Docker_files/Tftp-server/Start.sh
     docker start Tftp-server
     exportfs -ra
 elif [ "$1" = 3 ]
  then
   #mount image to dedicated dir  (reboot server start)
    umount "$loopdev"p1; umount "$loopdev"p2
    echo "$(grep -v $mountpoint /etc/exports)" > /etc/exports
    exportfs -ra
    losetup -d $loopdev
   sleep 1
    losetup -P "$loopdev" $outputimage
    echo "filesystem check"
    e2fsck -f "$loopdev"p2
    mount -o rw "$loopdev"p2 $mountpoint
     echo
"$mountpoint   *(rw,fsid=$rasbarrynr,no_subtree_check,async,no_root_squ
ash)" >> /etc/exports
     exportfs -ra 
    echo "restart tftp server"
    sh /mnt/bigpart/Docker_files/Tftp-server/Start.sh
   else 
  echo "input option 1,2 or as 1=reinstall, 2=boot, 3=reboot"
fi

echo "done preinstall script"

#umount "$loopdev"p1;umount "$loopdev"p2;losetup -d "$loopdev"; losetup
-a