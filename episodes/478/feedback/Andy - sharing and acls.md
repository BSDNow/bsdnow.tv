Hi BSD Now team,

Firstly, thank you for your dedication to both the BSD Now channel and the BSDs (especially FreeBSD & OpenBSD) in general.

I have been a passionate advocate of both OpenBSD (since ~4) and FreeBSD (since ~9), contributed many tests and bug reports over the years, and enjoy your sessions as often as I can.

There is one topic that I have been hoping would be answered over time (by anyone somewhere), but alas, after many years there still seems to be unclear consensus on how to make Samba run as fast as Netatalk on FreeBSD with ZFS for Mac clients.

It was several years ago now that Apple announced they were going to drop AFP for SMB.. Ok, I thought that finally the Samba client implementation on MacOS would get a much needed overhaul (Windows clients using SMB have always been faster than MacOS using SMB, but none as fast as AFP).

Over the years the mac client has had various issues, but it is now considered stable by Apple (there have not been any changes to the samba client for a while now).. Ok, so its down to the server side for now..

There have been a whole bunch of small changes including things like character set changes in MacOS that came with APFS, which should have removed the need for SMB to translate char codes when transferring from disk to SMB (and visa versa). There were various locking fixes and other things that Apple is shy to share.. Slowly but surely SMB on Mac has been getting faster.

At the same time, with each release of FreeBSD and Samba, I have been trying to tune/optimise the Samba configuration on ZFS. But there are two outstanding questions which I would love your opinions / debate on?

What is the current status of Sendfile support for FreeBSD with ZFS? Sendfile provides a notable performance boost on Linux by avoiding various locks and giving more direct access (my understanding is vague), but Sendfile support reportedly did/does not seem to work on freeBSD with ZFS. However I suspect this has changed with all the OpenZFS changes?

What is the current status of extended attribute support as system attributes (storing apple resource forks into ZFS SA's - which are MUCH faster than Apple Double's that are just hidden folders etc). For a long time, setting the ZFS pool extended attribute setting to 'sa' did nothing on FreeBSD.. I believe this might have changed in recent versions of FreeBSD again since the OpenZFS changes. Is this true?

And a final question for a fun debate? AFP is supposed to be dead as per-Apple, but it just wont die because Netatalk (on FreeBSD with ZFS) is still much faster than SMB.. I wonder, if SMB could use Sendfile (that worked properly with ZFS caches and (L2)ARC etc), and System Attributes for Extended Attributes (so icons can be set on folders and other mac specific things) worked, would the world finally be able to actually move to SMB for Mac clients?

Bonus questions.. Could discuss what is a recommended ACL setup for ZFS with SMB.. I have many notes at home on how to configure ACLs for ZFS, but I am unclear about the correct Samba settings for performance. Could also mention things like, don't change the TCP settings in smb.conf on FreeBSD like many blog posts suggest (as FreeBSD has a good network stack/auto detect settings already). Best aio settings for ZFS (should it be 0 or 16k). And finally 'vfs objects'..... I hear so many inconsistent things about what these module stacks should be.

And one final bonus general topic. The maxusers sysctl is set dynamically according to how much memory you have, and many other settings are derived from this setting. So you could say that maxusers is somewhat of a master knob.. setting this higher does improve performance for various things, but what if you have only a few users, and you want the MAX possible performance for those few users. Should this value be as high as possible or as low as double your user count etc (and you have to manually tune other knobs to improve the per-user performance). ZFS is generally optimised for many users, but how to make it faster for a few users..

Thanks for your time and thoughts.
All the best,
Andy Lemin
