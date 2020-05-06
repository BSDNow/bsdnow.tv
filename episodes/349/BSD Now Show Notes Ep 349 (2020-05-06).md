
***INFORMATIONAL ONLY***

Title:

Description:

Date: 2020-XX-XX

Tags: freebsd, openbsd, netbsd, dragonflybsd, trueos, trident, hardenedbsd, tutorial, howto, guide, bsd, interview, … ADD NEW TAGS FOR EACH EPISODE




***NOTES***

## Headlines
### [EKCD - Encrypted Crash Dumps in FreeBSD](https://oshogbo.vexillium.org/blog/74/)
> Some time ago, I was describing how to configure networking crash dumps. In that post, I mentioned that there is also the possibility to encrypt crash dumps. Today we will look into this functionality. Initially, it was implemented during Google Summer of Code 2013 by my friend Konrad Witaszczyk, who made it available in FreeBSD 12. If you can understand Polish, you can also look into his presentation on BSD-PL on which he gave a comprehensive review of all kernel crash dumps features.
> The main issue with crash dumps is that they may include sensitive information available in memory during a crash. They will contain all the data from the kernel and the userland, like passwords, private keys, etc. While dumping them, they are written to unencrypted storage, so if somebody took out the hard drive, they could access sensitive data. If you are sending a crash dump through the network, it may be captured by third parties. Locally the data are written directly to a dump device, skipping the GEOM subsystem. The purpose of that is to allow a kernel to write a crash dump even in case a panic occurs in the GEOM subsystem. It means that a crash dump cannot be automatically encrypted with GELI.
***


!!!NOTES FOR ALLAN AND BCR!!!
!!!This is a very long article, I'd give it a quick scan before the show and pick one out section you want to highlight. It's a great article, but would probably take 10-20 minutes to do it justice if you read through the whole thing. So just covering one part and then telling people to see the article for the rest is probably the best way for us to go.!!!

### [Time on Unix](https://venam.nixers.net/blog/unix/2020/05/02/time-on-unix.html)
> Time, a word that is entangled in everything in our lives, something we’re intimately familiar with. Keeping track of it is important for many activities we do.
> Over millennia we’ve developed different ways to calculate it. Most prominently, we’ve relied on the position the sun appears to be at in the sky, what is called apparent solar time.
> We’ve decided to split it as seasons pass, counting one full cycle of the 4 seasons as a year, a full rotation around the sun. We’ve also divided the passing of light to the lack thereof as days, a rotation of the earth on itself. Moving on to more precise clock divisions such as seconds, minutes, and hours, units that meant different things at different points in history. Ultimately, as travel got faster, the different ways of counting time that evolved in multiple places had to converge. People had to agree on what it all meant.
See the article for more
***



## Interview - name - [email@email](mailto:email@email) / [@twitter](https://twitter.com/user)
Interview topic
+ BR: ?
+ AJ: ?

***

## News Roundup
### [Improve ZVOL sync write performance by using a taskq](https://github.com/openzfs/zfs/commit/0929c4de398606f8305057ca540cf577e6771c30)
***

### [A central log host with syslog-ng on FreeBSD - Part 1](https://blog.socruel.nu/freebsd/a-central-log-host-with-syslog-ng-on-freebsd.html)
> syslog-ng is the Swiss army knife of log management. You can collect logs from any source, process them in real time and deliver them to wide range of destinations. It allows you to flexibly collect, parse, classify, rewrite and correlate logs from across your infrastructure. This is why syslog-ng is the perfect solution for the central log host of my (mainly) FreeBSD based infrastructure.
***

### [HEADS UP: NetBSD Entropy overhaul](https://mail-index.netbsd.org/current-users/2020/05/01/msg038495.html)
> This week I committed an overhaul of the kernel entropy system.  Please let me know if you observe any snags!  For the technical background, see the thread on tech-kern a few months ago: <https://mail-index.NetBSD.org/tech-kern/2019/12/21/msg025876.html>.
***

### [Setting Up NetBSD Kernel Dev Environment](https://adityapadala.com/2020/04/20/Setting-Up-NetBSD-Kernel-Dev-Environment/)
> I used T_PAGEFLT’s blog post as a reference for setting my NetBSD kernel development environment since his website is down I’m putting down the steps here so it would be helpful for starters.
***

## Beastie Bits
[You can now use ccache to speed up dsynth even more.](https://www.dragonflydigest.com/2020/05/04/24480.html
[Improving libossaudio, and the future of OSS in NetBSD](http://blog.netbsd.org/tnf/entry/improving_libossaudio_and_the_future)
[DragonFlyBSD DHCPCD Import dhcpcd-9.0.2 with the following changes](http://lists.dragonflybsd.org/pipermail/commits/2020-April/769021.html)
***

## Feedback/Questions
+ Ghislain - [ZFS Question](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/349/feedback/Ghislain%20-%20ZFS%20Question.md)
+ Jake - [Paypal Donations](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/349/feedback/Jake%20-%20Paypal%20Donations.md)
+ Oswin - [Hammer tutorial](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/349/feedback/Oswin%20-%20Hammer%20tutorial.md)

***
- Send questions, comments, show ideas/topics, or stories you want mentioned on the show to [feedback@bsdnow.tv](mailto:feedback@bsdnow.tv)
***


