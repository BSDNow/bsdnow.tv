A question for the show…

Motivated to update the networking for my jails since in FreeBSD 13.0 “/32” netmasks do not work the way they do in earlier releases (see Bug 258949).

If the old way of doing it was,

rc.conf:
ifconfig_cc0="inet 129.174.130.140/27"
ifconfig_cc0_alias0="inet 129.174.130.141/32"

jail.conf:
ip4.addr=129.174.130.141;

Is this the correct way now,

ifconfig epair create
ifconfig bridge create
ifconfig bridge0 addm epair0a up
ifconfig bridge0 addm cc0 add epair0b

rc.conf:
ifconfig_cc0="inet 129.174.130.140/27"

jail.conf:
ip4.addr=129.174.130.141/27;
interface=epair0b;
