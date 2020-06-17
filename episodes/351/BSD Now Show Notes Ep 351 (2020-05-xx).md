
***INFORMATIONAL ONLY***
Title:
Description:
Date: 2020-XX-XX
Tags: freebsd, openbsd, netbsd, dragonflybsd, trueos, trident, hardenedbsd, tutorial, howto, guide, bsd, interview, … ADD NEW TAGS FOR EACH EPISODE

***NOTES***
## Headlines

### [Backup and Restore on NetBSD](https://e17i.github.io/articles-netbsd-backup/)

> Putting together the bits and pieces of a backup and restore concept, while not being rocket science, always seems to be a little bit ungrateful. Most Admin Handbooks handle this topic only within few pages. After replacing my old Mac Mini's OS by NetBSD, I tried to implement an automated backup, allowing me to handle it similarly to the time machine backups I've been using before. Suggestions on how to improve are always welcome.
 
***

### [BSD Release: OpenBSD 6.7](https://distrowatch.com/?newsid=10921) 
> The OpenBSD project produces and operating system which places focus on portability, standardisation, code correctness, proactive security and integrated cryptography. The project's latest release is OpenBSD 6.7 which introduces several new improvements to the cron scheduling daemon, improvements to the web server daemon, and the top command now offers scrollable output. These and many more changes can be found in the project's release announcement: "This is a partial list of new features and systems included in OpenBSD 6.7. For a comprehensive list, see the changelog leading to 6.7. General improvements and bugfixes: Reduced the minimum allowed number of chunks in a CONCAT volume from 2 to 1, increasing the number of volumes which can be created on a single disk with bioctl(8) from 7 to 15. This can be used to create more partitions than previously. Rewrote the cron(8) flag-parsing code to be getopt-like, allowing tight formations like -ns and flag repetition. Renamed the 'options' field in crontab(5) to 'flags'. Added crontab(5) -s flag to the command field, indicating that only a single instance of the job should run concurrently. Added cron(8) support for random time values using the ~ operator. Allowed cwm(1) configuration of window size based on percentage of the master window during horizontal and vertical tiling actions."

+ [Release Announcement](https://marc.info/?l=openbsd-announce&m=158989783626149&w=2)
+ [Release Notes](https://www.openbsd.org/67.html)

***



## News Roundup


### [Building a WireGuard Jail with the FreeBSD's Standard Tools](https://genneko.github.io/playing-with-bsd/networking/freebsd-wireguard-jail/)

>Recently, I had an opportunity to build a WireGuard jail on a FreeBSD 12.1 host.
> As it was really quick and easy to setup and it has been working completely fine for a month, I’d like to share my experience with anyone interested in this topic. 
 
***

### [The Unix divide over who gets to chown things, and (disk space) quotas](https://utcc.utoronto.ca/~cks/space/blog/unix/ChownDivideAndQuotas)

> One of the famous big splits between the BSD Unix world and the System V world is whether ordinary users can use chown (the command and the system call) to give away their own files. In System V derived Unixes you were generally allowed to; in BSD derived Unixes you weren't. Until I looked it up now to make sure, I thought that BSD changed this behavior from V7 and that V7 had an unrestricted chown. However, this turns out to be wrong; in V7 Unix, chown(2) was restricted to root only.
 
***

### [Using qemu guest agent on OpenBSD kvm/qemu guests](https://undeadly.org/cgi?action=article;sid=20200514073852)

> In a post to the ports@ mailing list, Landry Breuil (landry@) shared some of his notes on using qemu guest agent on OpenBSD kvm/qemu guests.
> 
***

### [You Can Influence the TrueNAS CORE Roadmap!](https://www.ixsystems.com/blog/truenas-bugs-and-suggestions/)

> As many of you know, we’ve historically had three ticket types available in our tracker: Bugs, Features, and Improvements, which are all fairly self-explanatory. After some discussion internally, we’ve decided to implement a new type of ticket, a “Suggestion”. These will be replacing Feature and Improvement requests for the TrueNAS Community, simplifying things down to two options: Bugs and Suggestions. This change also introduces a slightly different workflow than before.
***

## Beastie Bits

+ [FreeNAS Spare Parts Build: Testing ZFS With Imbalanced VDEVs and Mismatched Drives](https://www.youtube.com/watch?v=EFrlG3CUKFQ)
+ [TLSv1.3 server code enabled in LibreSSL in -current](https://undeadly.org/cgi?action=article;sid=20200512074150)
+ [Interview with Deb Goodkin](https://itsfoss.com/freebsd-interview-deb-goodkin/)
***

## Feedback/Questions

+ [Bostjan - WireGaurd](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/351/feedback/Bostjan%20-%20WireGaurd.md)
+ [Chad - ZFS Pool Design](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/351/feedback/Chad%20-%20ZFS%20Pool%20Design.md)
+ [Pedreo - Scale FreeBSD Jails](https://github.com/BSDNow/bsdnow.tv/blob/master/episodes/351/feedback/Pedreo%20-%20Scale%20FreeBSD%20Jails.md)

***

- Send questions, comments, show ideas/topics, or stories you want mentioned on the show to [feedback@bsdnow.tv](mailto:feedback@bsdnow.tv)

***


