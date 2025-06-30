Hello, team,

I have two NAS boxes on my network. On the primary (luna), I am testing out zVault 13.3. It was running TrueNAS Core 13.0u6.7 (latest version) prior to that. The secondary NAS, intrepid, is running the 13.3 version of TrueNAS Core. I am doing a pull replication of all of the datasets, from luna to intrepid.

Since I need to rebuild the pool on luna (it is still using GELI), I went the next logical step, and created the NFS shares on intrepid  (through the gui, of course) and set up commented out fstab entries for intrepid on the client boxes.

However, at midnight, when the middleware does whatever it does (the only thing I see in /etc/crontab is a restart of syslog-ng, but that is not the problem), mountd is throwing errors on several of shared daasets. I get "bad exports list line" on several of them, and "netcred already exists for given addr/mask"

bad exports list line '/mnt/NCC1631/luna/backuppc -maproot'
bad exports list line '/mnt/NCC1631/luna/iso danube defiant'
bad exports list line '/mnt/NCC1631/luna/library defiant danube valiant'
bad exports list line '/mnt/NCC1631/luna/media -alldirs -network 192.168.47.0/24'
bad exports list line '/mnt/NCC1631/luna/software defiant danube'
bad exports list line '/mnt/NCC1631/luna/video_clips -alldirs defiant danube 172.20.100.2'
can't change attributes for /mnt/NCC1631/luna/backuppc: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna/iso: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna/library: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna/media: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna/software: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna/video_clips: netcred already exists for given addr/mask
can't change attributes for /mnt/NCC1631/luna: netcred already exists for given addr/mask


So I get these errors triggered at midnight immediately after syslog-ng reloads. I tested setting up one host to nfs mount on intrepid. When the errors fired, that host was unable to access the data on the dataset, although the nfs mount still existed. I get the following error on the host mounting from that dataset:

May 10 00:00:24 defiant kernel: newnfs: server 'intrepid' error: fileid changed. fsid 0:0: expected fileid 0x22, got 0x2. (BROKEN NFS SERVER OR MIDDLEWARE)

 I have been through my configs numerous times, comparing between luna and intrepid. I even upgraded intrepid to zVault 13.3, for an apples-to-apples comparison. I have gone through every setting, comparing between luna that is working and intrepid that is not. The only thing I found was that the ACL Mode setting for the pool on intrepid was not set, likely because I ended up building the pool on XigmaNAS and possibly missed that setting, or it was not available when I created the pool. But I set it in the pool and it cascaded down, but hte mountd problems persist.

Do you have any ideas what may be causing the problem on one NAS but not the other? It seems like something deep down in the weeds of either NFS or TrueNAS.

Thanks,
--b
