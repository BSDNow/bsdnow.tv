Allan,

I recently acquired a Dell R610 with Dual Xeon/96GB of RAM and 3 x HP
D2600 fully populated with LFF 2TB drives (72TB RAW total) for my home
lab. I'm planning to replace the six internal R610 SFF drives with SSD
and use two for mirrored zroot (quick question about that, can I build
zroot on HDD and replace with SSD or should I really build with SSD
from the start?) and the other four for SLOG/L2ARC.

I've purchased the storage bundle on MWL's website in hopes of gaining
some insight into how to slice and dice the drives up. I'm currently
reading FreeBSD Mastery: ZFS book and certainly picked up some good
tips so far, such as drive labeling and ensuring zdevs are spread
across enclosures, but I'm still unsure of how to configure the
pools/zvdevs for this setup. The primary purpose of this system will
be hosting Plex and running other jails and/or bhyve instances to
provide some additional services (e.g. git repos, munin, nfsen,
LibreNMS, Prometheus/Grafana, ELK, Suricata/Bro, etc.) as well as
experiment with new apps/tech.

What would you recommend in terms of vdev/pool configuration for this setup?

Thanks,

Chad