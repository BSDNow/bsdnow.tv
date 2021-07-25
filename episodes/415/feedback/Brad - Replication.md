Hi Allan, JT, Benedict, and Tom, (In order of arrival on BSD Now?)

I have a FreeBSD laptop and desktop, both running 13-RELEASE. Both are running snapshots out of cron using zfstools. So I have a year of snapshots on both machines. And when I set up zfstools, I turned off snapshotting in places where I thought I wouldn't need them, like

NX72003/iocage/download
NX72003/iocage/releases
NX72003/usr/ports
NX72003/tmp
NX72003/var/crash
NX72003/var/tmp

...Basically things that are a) likely to take up except space, b) are freely available on the internet...So I am only snapshotting certain datasets. Which leads to my problem. I am trying to do a pull replication from the desktop and laptop to my TrueNAS box. As an example, I have snapshots on the following datasets:

NX72003
NX72003/iocage
NX72003/iocage/images
NX72003/iocage/jails
NX72003/iocage/jails/testbox
NX72003/iocage/log
NX72003/iocage/templates
NX72003/ROOT
NX72003/ROOT/13.0-RELEASE_2021-06-06_210348
NX72003/ROOT/default
NX72003/usr
NX72003/usr/git
NX72003/usr/home
NX72003/usr/ports
NX72003/var
NX72003/var/audit
NX72003/var/log
NX72003/var/mail

I know that if I could set up 18 different replication tasks on the TrueNAS box, but is there a way to combine that into one task and push (or pull) all of the datasets in one operation? Simebody on the forums suggested using syncoid, but that isn't going to work, because syncoid doesn't ship on TrueNAS.

Can I get your suggestions on this?

Thanks,
--b
