

Is there an article or can you give the commands to backup $HOME like on a laptop that has ZFS to a local USB drive.  The laptop doesn't have access to like a on premises backup server.  Grant it I already backup to tarsnap but would like to automatically save that tarsnap backup and maybe more to a usb drive and maybe dedup there as well. Would it be as simple as to copy over the tar file?  Is there a better way to backup ones $HOME to a USB drive.  My tarsnap is only critical data but I would like to backup the entire $HOME to a local USB drive.  I can tar it up and copy to the USB drive but that doesn't seem very efficient since it takes forever++; to overwrite the existing tar I would like to just update what's there that has changed.  Maybe some ZFS magic or something would be in order.  I don't need to backup the entire system just /etc and other configs and $HOME.  Remember this is not a server just a users laptop for local use only.  Anyway any help would be very much appreciated.