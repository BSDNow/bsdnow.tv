Howdy, magic voices in my ears!

First, thank you for this wonderful weekly update! I sub many podcasts, but you're the only one that gets auto-added to the TOP of my queue.

Secondly, thank you to Benedict especially - some of your `fortune` contributions have saved me more time than I can I measure.

Lastly, a question: What is a good, safe way to update dozens of jails in bulk? I have a host with 30-40 jails on it, some of which run production databases that will occasionally break if I forget to stop the database service before doing a pkg update. Is it possible to bring jails down into something like single-user mode? Or maybe just stop them entirely and use `pkg --chroot $JAIL_PATH` or `pkg --root $JAIL_PATH`? Today I'm using a very ugly while loop with the following:

```
service -e 2>/dev/null \
| grep -F '/usr/local/etc/rc.d/' \
| cut -d'/' -f6 \
| while read SERVICE_RC; do service $SERVICE_RC stop; done
```

I feel like there MUST be a better way to do this? How are other with more-than-just-a-few-jails keeping service jails updated without ripping rugs out from underneath sensitive runtimes?

Thanks again,

Dan
