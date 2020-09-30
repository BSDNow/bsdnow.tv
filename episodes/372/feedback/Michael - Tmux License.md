 Allan and Benedict (and JT and all other contributors),

I was listening to episode 367 and just wanted to let you guys know that while screen is definitely GPL, tmux is ISC-licensed.  I might be wrong, but think that would mean it's allowed to be in the base system (BIND was ISC until v9.11 and it was included, right?).  So, maybe it could be installed by default...?
That'd be pretty cool, since it's definitely part of a lot of peoples' basic toolbox. Then again, so are cURL (MIT/Xish) and zsh (MIT but for some GPL shell functions), which may not really belong in base or would require tweaking beforehand. 

When I heard that I never need to use telnet again if curl is installed, I welled up with tears a little. "curl telnet://HOSTNAME_OR_IP:PORT" does the same thing as "telnet HOSTNAME_OR_IP PORT".  Adding -v for verbose and/or "--connect-timeout 3" makes it even better because if your target hostname has multiple A records and gets a failure, it'll try them all. Also, timing out automatically means no need for a Ctrl+(d|c|^|whatever) to get back to your shell. Pretty neat.

Anyway, just some food for thought.  Thanks for the wonderful show!

~ Michael