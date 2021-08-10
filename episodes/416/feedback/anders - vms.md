
Hi Allan, Benedict, Tom and JT

Long time listener, second time emailer, enjoying the show every week.

I was wondering if you could shine some light on what happened with my zfs pool recently. It's a FreeBSD 13 system, upgraded from 12 and the pool has been upgraded.

It might be easiest to explain what happened in a sequence of events.

I opened the laptop lid and was greeted with a kernel panic caused by VirtualBox. I knew this can happen and should have stopped my VM's before I closed the lid the previous day.

The stack trace filled my screen line by line very slowly so I decide to just hold down the power button to force a power off.

Once restarted, X didn't start and dmesg showed that another 2-3 processes had crashed with the error "vm fault: pager read error"

I restarted one of the failed processes and oddly enough it seems to have started OK.

"zpool status" showed 2 checksum errors and the status text "One or more devices has experienced an error resulting in data corruption.  Applications may be affected"

I ran "zpool scrub" and when it finished showed almost 5 thousand checksum errors.

I turned the computer off, removed the SSD and reinserted it to make sure it was pushed in properly.

I started the computer again and "zpool status" now said 0 checksum errors and 450 data errors. "zpool status -v" showed that some pictures were corrupted but they opened up without any visible corruption or complaints in dmesg.

I ran "zpool scrub" again and after it was finished the pool was reported as completely healthy, no checksum or data errors. It also said that scrub repaired 0B with 0 errors.

What happened here? Is the force power off during the panic likely to be related? Was it just the SSD drive not making proper contact and resitting it resolved it?

Keep up the good work.

Thanks,
Anders
