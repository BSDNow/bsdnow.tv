Hey guys! Love the show, keep it up. Glad Alan is back, but it was also nice to have some different voices on the show too (:

Question: I am a little bit lost about how ZFS caching with respect to writes works. I asked this clarification a while back on Reddit and got an incredibly generous and detailed reply from a user named txgsync (thanks txgsync if you're listening!!) - but I was hoping you could try to confirm that what he traced is still the behaviour in current ZFS? That is, "when a transaction acquires a DVA due to allocation via the txg -> dmu_tx -> spa path, they are migrated onto the arc_mru list" - a transaction group that has just been synced to disk does, in fact, remain in ARC until evicted and can, thus, be read from ARC. Also hoping for discussion on where I can learn about what tuning can be adjusted to encourage the MRU to stay in ARC or L2ARC longer.

Also a side note - It would be great if you guys put a big button somewhere on the bsdnow.tv homepage on how to send in these questions (e.g., "ASK A QUESTION, GET AN ANSWER ON THE SHOW! CLICK HERE"), since you ask for more questions on the show. Every time I've gone to try and submit something I find myself hunting around a bit. It's not hard, to be fair, but I'm not entirely sure I'm even submitting it in the right place.

Thanks,

~Micah