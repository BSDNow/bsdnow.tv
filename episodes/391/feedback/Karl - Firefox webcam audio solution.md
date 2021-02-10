Hi guys,

I emailed you a couple of months ago about problems with webcam audio and video conferencing on Firefox.

I thought I'd follow up with a solution to the problem I was having in case it's of use to your other listeners.

The problem I was having was that sometimes the microphone on my webcam would stop working with Firefox. I finally realiased what was going wrong when I ran "pkg info -D firefox".

When Firefox was using OSS, everything worked. But if I installed a package that installed sndio as a dependency (such as Chromium), Firefox would switch to using sndio and only the default playback and recording device would work. As my webcam microphone was on /dev/dsp3, it would not be picked up by default.

Running "pkg info -D firefox" explains that there is a Firefox configuration option "media.cube.backend" that can be used to choose your audio backend. I set it to OSS and now everything works as expected. I can choose playback and recording devices before I start a conference call.

Hope this helps someone out there!

Thanks,
