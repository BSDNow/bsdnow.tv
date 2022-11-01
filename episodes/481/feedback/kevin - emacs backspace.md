Hi BSD Now Crew,

Really enjoy the show. Sorry for the double-post in September repeating my question from August. It's worth waiting for your response, and could help out another listener too. (This time, I'll wait 8 weeks before I assume my first message was missed.)

'stty -a' showed erase already set to ^?. But erase2 was set to ^H. The following command successfully set erase2 to ^? both on the command line and when added to ~/.cshrc.

$ stty erase2 '^?'

But that made no difference for using backspace in mg or Emacs. It simply passed Ctrl-h to the application. Ctrl-Backspace does properly delete the character to the left of the cursor in the normal backspace fashion.

After applying the change, logging out of all tmux and ssh sessions and even rebooting made no difference.

This happened on my Thinkpad T440 laptop 2 years ago when I tried FreeBSD on it, and currently happens in the direct consoles of VirtualBox, Digital Ocean, and Vultr - everywhere I've run FreeBSD (over SSH doesn't have this problem).

What further info would I need to file a bug report?

Thanks and keep up the great show.
Kevin 