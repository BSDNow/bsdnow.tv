

Although it's not an issue on a desktop machine where I have external speakers with their own volume control, an issue I have on my laptop is that sometimes the volume is not loud enough even when I turn it all the way up in software (i.e. Kmix under Plasma 5) and even when I set hw.snd.vpc_0db=1 with sysctl. I tried the mixer command and found that the value of mix was 75. Setting it to 100 helped some. Is there anything else I can do to boost volume in FreeBSD?

