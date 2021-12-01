Hello Allan and Benedict and Tom and JT,

I am having a bit of an issue getting linux binaries to run on a FreeBSD 13 desktop. I recently purchased Kerbal Space Program (KSP) from Good Old Games (GOG). I got the Linux code as well as the windows code. Wine appears to be so broken on FreeBSD that I am unable to install KSP from the wine installer. So I opted to attempt to install the linux version of the program.

I tried several things to get Kerbal running, but I feel like I am missing (or have overlooked) something critical. I have been following the Linuxulator page, and according to the first tried to the linux-c7 directory tree in /compat/linux. I then tried building an ubuntu tree in /compat/ubuntu. That didn't work either, so I built a devuan linux (debian minus the systemd portion). None of these worked, so I set up a devuan linux jail in iocage. When I try to ssh -XY in to the jail and launch Kerbal (or even glxgears), I get an X error:
		
storm@brahms:/var/log$ glxgears
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  151 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  31
  Current serial number in output stream:  32
When I use the /compat tree, I start the application, and it seems to just hang there. Can you suggest what I might be missing here?

Thanks,
--b
