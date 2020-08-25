Hi Allan, Benedict and JT,

Thank you very much for you EXCELENT show!

Would you be so kind and answer ZFS question? Or two  ?

All related to Debian 10 (soooory!!) with ZFS 0.8.4.

1. QUESTION
Could you please confirm that it is not possible to send/receive whole pool when it's encrypted?

When I do this:

~~~~~~~~~~~~~~~~~~
sudo zfs snapshot -r mybigpool@send_this
sudo zfs send -R -w mybigpool@send_this | ssh secondaryserver001 sudo zfs receive -d -F -u -v mybigpool
~~~~~~~~~~~~~~~~~~

I get that:

~~~~~~~~~~~~~~~~~~
cannot receive new filesystem stream: zfs receive -F cannot be used to destroy an encrypted filesystem or overwrite an unencrypted one with an encrypted one
~~~~~~~~~~~~~~~~~~

Based on my understanding when I create a new pool, the root dataset is always created (I can't create new pool without the first/root dataset) and because it already exists, I can't use zfs receive -F since -F can't be used with encryption when the destination dataset already exists.

Which means the only option is to send one-by-one datasets one level below the root dataset.

~~~~~~~~~~~~~~~~~~
sudo zfs send -R -w mybigpool/first@send_this  | ssh secondaryserver001 sudo zfs receive -F -u -v mybigpool/first
sudo zfs send -R -w mybigpool/second@send_this | ssh secondaryserver001 sudo zfs receive -F -u -v mybigpool/second
sudo zfs send -R -w mybigpool/third@send_this  | ssh secondaryserver001 sudo zfs receive -F -u -v mybigpool/third
~~~~~~~~~~~~~~~~~~

2. QUESTION
I know that there are many very good auto-snapshot/auto-send tools like for example sanoid and syncoid. But I like simplicity and I'm thinking about VERY simple cron job that would run for example every morning to backup my server:

~~~~~~~~~~~~~~~~~~~~~
FIRST_SNAPSHOT_NAME='20200101-120000-first_snapshot_ever'
NEW_SNAPSHOT_NAME=$(date --utc +%Y%m%d-%H%M%S)

# first manual send before this cron job that will create "mybigpool/first" on receiving side
# sudo zfs snapshot -r "mybigpool/first@$FIRST_SNAPSHOT_NAME"
# sudo zfs send -R -w "mybigpool/first@$FIRST_SNAPSHOT_NAME" | ssh secondaryserver001 sudo zfs receive -F -u -v mybigpool/first

sudo zfs snapshot -r "mybigpool/first@$NEW_SNAPSHOT_NAME"
sudo zfs send -R -w -i "$FIRST_SNAPSHOT_NAME" "mybigpool/first@$NEW_SNAPSHOT_NAME" | ssh secondaryserver001 sudo zfs receive -F -u -v mybigpool/third
~~~~~~~~~~~~~~~~~~~~~

The first problem is that the script doesn't remove old snapshots but since it will run only once a day it will create 365 snapshots a year and I can setup some monitoring for free disk space and remove all snapshots manually when needed.
The second problem is that I'm not sure if it's cool to use always "-i same_snapshot_name" but if it's not I can do something like that:
~~~~~~~~~~~~~~~~~~~~~
PREVIOUS_SNAPSHOT=$(ssh secondaryserver001 sudo zfs list -d 1 -t snapshot -H -o name mybigpool/st | tail -n 1 | sed 's|.*@||')
sudo zfs snapshot -r "mybigpool/first@$NEW_SNAPSHOT_NAME"
sudo zfs send -R -w -i "$PREVIOUS_SNAPSHOT" ...
~~~~~~~~~~~~~~~~~~~~~
It will make the whole script more fragile but in the worst case I get an e-mail about failed cron and I'll login to fix it.

THANK YOU VERY MUCH!!!

Kind regards,
Ben