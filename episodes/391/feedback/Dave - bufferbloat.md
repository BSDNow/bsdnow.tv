hey folks!

Now that I have 2.5 kids doing school from home, 1 partner full-time videoconferencing, and NO PEACE FOR MY OWN WORK BECAUSE OF CONSTANT SHADOW IT REQUESTS, I need to address the elephant in the room - network instability due to bufferbloat.

I finally have enough (asymmetric) bandwidth for this to be a problem, and while I dealt with this neatly on my OpenBSD firewall using https://man.openbsd.org/pf.conf.5#QUEUEING I'm not clear how to achieve the same outcome with FreeBSD.

Do you have any tips about dealing with bufferbloat, and perhaps using codel or cake algorithms on FreeBSD? Do I need a custom kernel (which I have successfully put off since now), with ALTQ?

link fodder for the show notes:

- https://bufferbloat.net/ the original description
- http://www.dslreports.com/speedtest a nice easy browser-based test for it
Dave Taht, the person who identified the issue, with 2 great talks and a solid PDF:
- https://youtube.com/watch?v=ZeCIbCzGY6k
- https://youtube.com/watch?v=Mxoa5Si4Ubw
- http://www.taht.net/~d/lca_tcp3.pdf

- https://www.reddit.com/r/HomeNetworking/comments/fvhr4w/psa_sqm_cake_nat_and_bufferbloat_tuning/

- https://youtube.com/watch?v=tuaH8DlYZcQ Ry may well be the youngest network engineer you know!

A+
Dave
