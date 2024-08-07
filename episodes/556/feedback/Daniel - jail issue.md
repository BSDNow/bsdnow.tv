Hello!

I posted this on the Telegram channel, but it sounds like maybe it’s better sent as a question here…..

I'm trying to deploy a service in a FreeBSD jail... (my first one at work as a POC).

It's a (commercial) java application that can present virtual filesystems via various protocols (sftp,smb,nfs...) to the outside world.

OpenJDK seems to need /dev/fd and /proc mounted in the jail so I have those to keep it happy.

I can connect directly to the jail from outside via normal ssh (i.e. sshd_enable="YES" in the jail), and to the sftp service from the java application so I think the networking is fine, but the userspace NFS presentation from the java application won't allow a connection, despite it showing up fine (port 9001 here along with the other java presentations and my iperf3 test for network speed)

e.g.
# sockstat -l4
USER     COMMAND    PID   FD  PROTO  LOCAL ADDRESS         FOREIGN ADDRESS      
root     java       23791 82  tcp4   *:80                  *:*
root     java       23791 83  tcp4   *:9001                *:*
root     java       23791 93  tcp4   *:2049                *:*
root     java       23791 104 tcp4   *:9003                *:*
root     iperf3     65206 3   tcp4   10.249.20.29:5201     *:*
root     sshd       47041 3   tcp4   10.202.9.72:22        *:*

There might be some subtle FreeBSD OpenJDK incompatibility causing a problem with the java application, but I wondered if there are some jailsy gotchas here, or does anyone have a suggestion for what I should explore to try to find a solution?

I'm being pressurised to move it all to Ubuntu but that rather goes against my normal routine of encouraging colleagues to consider BSD.... 🙂

Thanks in advance for any help/suggestions, and thanks for the great podcast!

Best wishes,

Daniel
