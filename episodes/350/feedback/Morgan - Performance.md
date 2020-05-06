Hi, JT. Here’s a question for Allan or Benedict (or you!) to answer on the next podcast...

I’m looking for a basic CPU/memory performance measurement tool so I can check the relative speed of my FreeBSD systems. I run several on DigitalOcean and my own hardware — even a bhyve instance. I like taking speed measurements before and after operating system and hardware upgrades to track variations in performance. For my purposes, the score doesn’t need to be a super scientific benchmark...just something that gives a basic idea of a machine’s speed. In the past, I turned to the old “ubench” tool for this. It runs for a few minutes and then outputs a single score for CPU and memory. It’s great for this, but it takes a while and tends to crash (especially in bhyve). Is there a simple alternative that is quick, convenient, and runs from a command line (no X windows)? 

What I have used in the past, to tell if my Digital Ocean droplet was on an overloaded machine (then I'd delete it and get a new one), was just the sha512 benchmark.

Now, that can be impacted by hardware having special code to make sha512 faster, but, there is a variant, sha512 truncated to 256, that ZFS uses, that has never been implemented in hardware.

sha512t256 -t

It will run for something like 2-5 seconds, and also outputs a speed that you can compare between machines.

It is quite basic, but, should give you a reasonable comparison. Note it only uses 1 CPU, so it will a score mostly based on ghz of one core.

As always, thanks!