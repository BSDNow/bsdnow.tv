
Hi Guys,

I've set up a backup replication of my zfs pool to a machine at my workshop using Jim Salter's syncoid tool. It is sent raw/encrypted and the key is never present on the workshop machine. It uses Cron to SSH into the main machine as a limited user, and do the zfs send (with appropriate permissions from zfs allow). I've tried to configure things so the backup machine has no access to the data at all, whether in its own zfs pool or when it is mounted on the main machine. While I can use FS permissions to prevent access to the mounted data, and I can tell syncoid to do a raw transfer, there seems to be no way to explicitly restrict a user to raw send only. If for instance someone gained access to my backup machine, although the existing data is encrypted they could just alter the send/recv commands to send it unencrypted from the main machine. 

I've not managed to find any way to restrict that ability. How do you work round this vulnerability?

Thanks

James
