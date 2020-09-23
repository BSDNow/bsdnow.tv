Possible topic for you next episode - rcorder.

rcorder appeared in netbsd around 1998. Together with /etc/rc it has been a solid way to reliably start services at boot - for over twenty years!

Not to say there's been no efforts to make improvements. Quite the opposite. The trouble is rcorder set the bar very high.

https://reviews.freebsd.org/rS309625 (committed)
https://reviews.freebsd.org/D15247 (committed)
https://reviews.freebsd.org/D19906 (abandoned)
https://reviews.freebsd.org/D3715 (abandoned)
https://reviews.freebsd.org/D25389 (approved)

See also my own efforts here which describe yet-another rcorder implementation but also include what, how, and why to change /etc/rc to support concurrency.

https://wiki.freebsd.org/unitrunker/rcorder

There's even more attempts at rewriting rcorder than I thought. 

Some highlights:

https://github.com/ultijlam/rcorder.sh (a POSIC shell rewrite of rcorder)
https://github.com/kil/rcorder (parallel rcorder updated to use a 'trampoline' supplemental script)
https://github.com/ngie-eign/rcorder3 (C++ rewrite of rcorder - with python unit tests)
https://github.com/buganini/rcexecr (move rc script invocation inside rcorder)

I looks forward to seeing Boris' D25389 'rcorder -p' very soon.