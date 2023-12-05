Brad 
Howdy guys,

I have been running FreeBSD for several years now, and I love it. However, one thing has been driving me crazy. When I started using FreeBSD in the 12.0 days, it seemed that there were only a few options for managing jails: building from scratch, warden, and iocage.

However, now, in the latter part of the 13.0, it seems like there are many, many jail managers...scratch jails, warden, iocage, cbsd, bastille, and so forth. There are enough that it seems most people end up finding and landing on a solution, and stay there, and migrating to a new solution is a non-trivial exercise.

So my use case is as follows. I have two machines that I use as jail hosts, and have several server machines set up as jails, mainly single-use bastion hosts (e.g. DNS, internal mail server, etc). I wrote a couple of scripts to give me the ability to migrate jails between the jail hosts and back them up to my NAS. However, I kind of get the sense that some of the newer systems like cbsd and bastille have a lot of these features baked in. Having said that, I want whatever I use to roll neatly into vanilla FreeBSD. I don't want a solution like, say, proxmox-ve, which is built on Debian, but is really it's own specialized appliance. Since one of the boxes I am currently using for this is my desktop machine, I don't want to "appliancie-ify" it.

Do you gents have enough familiarity  with some or all of the tools to do a side-by-side comparison? I have looked online, but it seems that everybody blogging about it has their own favorite, and hasn't looked outside their own comfort zone. I would like to hear you all discuss, if possible, the pros and cons of the different jail managers.

Thanks,
--b
