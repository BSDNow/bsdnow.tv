
I finally have gotten around to setting up my headphone jack on my Dell
XPS in FreeBSD, and so far it works great.  Plugging my headphones into
the jack switches audio over.

But my headphones are also a headset with a built in mic and I'd like to
use that in FreeBSD as well but I'm getting stuck.  I am pretty sure
that my headphone jack supports this (the image next to the jack is
headphones with a boom mic attached, and I'm pretty sure headphone jacks
have supported this for years).

I've attached my dmesg from a verbose boot but in case that doesn't
work, here is the output:

hdaa0: Patched pins configuration:
hdaa0: nid   0x    as seq device       conn  jack    loc        color   misc
hdaa0: 18 b7a60130 3  0  Mic           Fixed Digital Lid-In     Unknown 1
hdaa0: 19 40000000 0  0  Line-out      None  Unknown 0x00       Unknown 0 DISA
hdaa0: 20 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 22 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 23 90170110 1  0  Speaker       Fixed Analog  Internal   Unknown 1
hdaa0: 24 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 25 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 26 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 27 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 30 411111f0 15 0  Speaker       None  1/8     Rear       Black   1 DISA
hdaa0: 33 04211020 2  0  Headphones    Jack  1/8     Right      Black   0

(note that this is before I setup headphones to work, I now put
Headphones on nid 33 into as 1).

Any tips?  I'm not even sure what to look for?  Maybe my jack as a
line-in ins just not supported?

My headphones have 3 bands on it.  It works as expected in a mobile
phone as well as my 10+ year old MacBook.  But I've never tested it in
another OS on my XPS to see if it works there.  I'm not quite sure how
to read the output of the table I sent in that is the Mic on nid18 just
the standard microphone on the laptop or does that correspond to the mic
input related to the jack?  I can see in the dmesg output:

pcm0: Microphone2 Volume (OSS: monitor): 0/30dB
pcm0:    +- ctl  3 (nid   7 in   0): -17/30dB (64 steps) + mute
pcm0:    +- ctl  6 (nid  18 out):    0/30dB (4 steps)

So there is nid 7 and nid 18?

Maybe I just need to figure out how to flip the mic input to nid 18 if
that corresponds to the jack input?

Thanks for the great show,
/Malcolm

