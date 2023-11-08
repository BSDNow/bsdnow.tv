
Hi gents,

I am working on a bit of a mystery. I am running zfstools to do cascading snapshots on all of my physical boxes. As recommended, I snapshot every 15 minutes and keep 4, then keep 24 hourlies, 7 dailies, 4 weeklies, and 12 monthlies, using the cleanup script to keep everything clean.

A couple of weeks ago, I was looking through my snapshots on my desktop machine running 13.2-RELEASE, and I noticed that some event happened at 2023-04-07.16:52:31, and
all of my monthly snapshots on that machine were destroyed for all datasets. Unfortunately, at the point where I found it, /var/log/messages only went back to 2023-04-26, and /var/log/cron only went back to 2023-05-25. I went back and searched for anything in my or root's command line history either from that time, or doing a zfs destroy, and found nothing.

My first instinct was to write an ansible playbook to actually write the zpool history (a lovely command that I just learned about while investigating this anomaly) to somewhere in /var for later analysis, but since it is stored permanently and appended to right within the pool, that seemed kind of pointless.

So I have two questions:
Is there a way to tell what caused almost a year of monthly backups to be deleted?
What would be the most straightforward way (since I already didn't know about zpool history) to detect, alert, or prevent something like this happening again? I guess I could write a script to check for anomalous destroys and then set up a cron job to run it on a regular basis through ansible or equivalent, but that seems a bit unweildy.

Thanks guys,
--b

