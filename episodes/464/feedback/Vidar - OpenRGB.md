
Hey lads, and thanks for making the podcast!
I have picked up a lot of good info from your show.

I have a story I would like to share with you:
When buying a new workstation for my home office, I ended up getting
a chassis with RGB LED lighting. The default mode for the LEDs is to
continuously cycle through all the colors, which can be quite distracting.

On my quest to control the lighting, I found out that these devices usually
need proprietary drivers that will surely never be available for us FreeBSD
users, but there is an open source project working to reverse-engineer them:
OpenRGB, https://openrgb.org.
However, its support was limited to Windows, Linux and MacOS, and trying to
build it on FreeBSD resulted in a barrage of compilation errors.

It's written in C++, which I know next to nothing about, but I like
a challenge so I went ahead with trying to add FreeBSD support to it.
It turned out to be easier than I had thought, although I did have to disable
support for a few lighting controllers due to compiler errors I was not able
to fix or work around.

Once I had it building and running, I cleaned up my changes and submitted
a merge request to add FreeBSD support, and it was accepted and merged!
We can now control RGB LED devices on FreeBSD \o/

I also submitted a PR for a port, which will hopefully have been committed
to the ports tree by the time you're reading this.

Call for help: as my C++ skills are lacking, I could not get the code for
GigabyteRGBFusion2GPU, HoltekA070 and HoltekA1FA to build, and thus had to
disable them. If anyone is interested and willing to give a helping hand,
any help to get these to build would be very much appreciated.

PS: There is also a plugin collection which I intend to port in the near
future, for those who like funky effects like sunrise, gradient waves,
bloom, rain and others. Our 2-year-old is very fond of the hypnotoad effect.

--
Colorful regards,
Vidar Karlsen
