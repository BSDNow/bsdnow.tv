Hi Everyone (AJ, BR, JT, TJ),
Thanks so much for what you do. I have been lurking around the edges of BSD space for the last 20 years and really enjoy keeping up to date through this podcast.
Apologies for the long rambling email but I've beening meaning to update my blog for around 10 years... but life happens, so here is a long rambling email for you  to enjoy :).
I was introduced to BSD when I bought a $100 2nd-hand PC from the computer science dept. at the university where I worked. The seller was demonstrating that the machine worked and booted etc and then proceeded to
cat /dev/zero > /dev/ada0 
To which I remarked "Oh is that linux, but why is the drive name funny?" They replied with "It's like linux but it's actually this thing called BSD..." I then went on to install FreeBSD on that machine and ran a GNUStep desktop for a number of years. I was always amazed at how clean, simple and fast the system felt to use, configure and maintain. Since then there has always been a BSD machine somewhere on my network.
I wanted to respond to some of the questions in episode 451: Tuning ZFS recordsize around modern laptops.
I've been running FreeBSD as my main laptop for around a year now and it's been a pretty good experience.

Currently running (among other things) a System76 Lemur Pro with a USB3 dock (Dell WD19S 180W) which runs 2 external monitors and provides Gigabit ethernet and USB hub etc..

I was luckily able to get some quirks into the 13.0 release to support the keyboard on the core-boot based laptop. I'm still poking about with the audio configuration (sysctl dev.hdaa) to get my  headphone audio to work perfectly, but generally I have a system for what I need, The warm fuzzy feeling running BSD gives me seems to far outweigh any of the current inconveniences.

I wanted to shout out to some of the ports that make running FreeBSD pretty much a non-issue for me.

net/wifibox/
Awesome port that will set up a tiny Alpine Linux VM using Bhyve (only 200Mb RAM) that will use PCI passthrough to run your wifi at full speed using the linux drivers. While it's been great to see my wifi card (Intel AC9560) supported in 13.1RC2 release, the speeds are still only at 54Mbps, this port allows me to run seamlessly at full speed.

sysutils/hw-probe
This probe gives you a really nice interface to what's on your system, what's supported and what's not. Having a poke around the website will allow you to find vendors that are well supported in BSD or Linux.The link  https://bsd-hardware.info/?view=computers&type=Notebook
will take you directly to a list of all the probes for laptops, you can also refine the search by manufacturer and year. My laptop is https://bsd-hardware.info/?probe=bbeb7d48fa

sysutils/acpi_call/
This port allowed me to write some simple scripts to access some BIOS features that would normally require some drivers somewhere for things like special function keys and charging thresholds that you often find on laptops. System76 being open source I was able to poke around their repositories for linux drivers and utilities to find the right parameters to talk to to get things done.

sysutils/barrier/ or sysutils/synergy/
If you have ever had two laptops and a desktop at your desk then either of these ports are like magic. I have been using this software for more than 20 years with almost every setup I've had. Being able to just place a laptop on the desk and mouse over to its screen from the desktop mouse and keyboard is simply awesome. It's not really a BSD thing, it's just useful when you want to put BSD on real hardware ( like an old macbook) while you continue to use the main computer for production work. It is a great way to play around with new things when a VM simply won't do it justice.

https://system76.com/

System 76 Lemur Pro has core boot and open source bios and embedded controller which means it has been pretty straight forward for me to add support to my FreeBSD setup for battery charge thresholds via the acpi-call port and permanently remap my CAPSLOCK key to CTRL in the firmware for the keyboard, although they now support a GUI for this.

More on Battery Thresholds.
I've attached my RC script for setting the battery thresholds. To ensure I get maximum lifespan out of my battery hardware I set my system to not start charging the battery until it is below 50% and when I'm at my desk most of the time I only ever top it up to 60% capacity. This means that the battery won't wear out after a couple of years where I spend most of my time sitting at my desk.When I know I'll be doing lots of portable work I'll set it to fully charge the battery. I've seen this feature come and go on other brand laptops in the past. It's nice to have the power to really configure your hardware how you want rather than the vendor maximizing for sales of new hardware.

I really like what this company is doing.. Open Hardware, Open Firmware, Open software, Full schematics available. And I'm lucky enough to be able to choose to pay a little more to give them my money rather than the likes of Lenovo and Dell. I also like the look of the Framework Laptops as well as they seem to be operating in the same spirit as System76. These are more than just a laptop being sold with linux on it.

--
Nick
