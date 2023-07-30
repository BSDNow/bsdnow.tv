Thank you for the great show. I enjoy your show for years and I'm always looking forward to it. You got me into zfs and BSD in general.

It's sad to see Alan go as a host, but Jason seems to be the perfect replacement. I'm excited for more OpenBSD insights!

I've a couple of questions surrounding the FreeBSD update process. (Upgrading OpenBSD is a breeze compared to FreeBSD.)

I've upgraded from 13.0 to 13.2 recently. I use the server as a jail host and NFS server.

0. Is is possible to upgrade a minor version from 13.0 to 13.2 directly?

1. 'uname -a' still shows the old verson (13.0). Is this normal or did I miss something?

2. What diff tool do you use with /bin/vi during the upgrade process? I basically just want to use the new files, unless I modified the file. Then keep the old file.

3. How do you upgrade your jails. What tools or process do you use? (I'm using iocage).

4. Since OpenBSD only supports NFSv3, do you use use NFSv4 at all across your servers or do you disable it?

Addendum to my previous email. This is the output regarding my first question. 

freebsd-version -r

13.0-RELEASE

freebsd-version -k

13.2-RELEASE-p1

freebsd-version -u

13.2-RELEASE-p1

uname -r

13.0-RELEASE

Thank you for helping me! Feel free to edit or change any question.

Keep up the amazing work!
Philip
