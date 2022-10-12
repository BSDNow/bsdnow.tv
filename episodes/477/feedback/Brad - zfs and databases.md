Hello Allan and Benedict and JT and Tom,

I have recently stood up a small FreeBSD machine to act as a life support system for jails to run my infrastructure hosts. I am using iocage. Some of these  jails use databases. I found a best practice stating that the optimal recordsize for PostgreSQL is 8k, and for MySQL is 16k.

So when I create a jail I will do something like

zfs create -o mountpoint=/usr/iocage/jails/root/spock
/var/db/postgres/data13 -o recordsize=8k NCC38907/iocage/jails/spock/pgsql

or

zfs create -o mountpoint=/usr/iocage/jails/root/sisko
/var/db/mysql -o recordsize=16k NCC38907/iocage/jails/sisko/mysql

I have a script set up to migrate jails between this server and my desktop machine, in the even tof an emergency, basically a wrapper around iocage export/import. So if I migrate a jail from one host to another, does that dataset get migrated with the jail to the new host? Or do I need to migrate the jail over to the new host and create and mount a parallel dataset? I also ask because my datasets have different names, based on the hostname.

Thanks,
--b