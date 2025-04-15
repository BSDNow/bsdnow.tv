
Hi BSDNow crew,

I just wanted to give a little follow up to my question about storage backends that you answered in episodes 586 and 594. I asked asked about using an S3-compatible backend or NFS to provide storage to services like Nextcloud.

Jason suggested that I look at iSCSI and pointed me to his recent FreeBSD journal article.

I found that iSCSI was easy to set up and saturated my 1G ethernet link without any tuning of the VM or host. Automatically mounting the iSCSI target on the VM was easily done using the _netdev option in the fstab file.

Thankyou for this suggestion.

Brendan.
