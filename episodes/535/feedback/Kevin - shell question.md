
Hi Benedict, Tom, Jason, and JT,

I miss Allan Jude. But I still get to hear him alongside Jim Salter on 2.5 Admins. BSD Now content has remained fun and engaging. Thank you Jason for stepping up.

After running FreeBSD on servers and accessing over SSH for a few years, I decided to try it on my laptop.

I discovered my preferred editors, Emacs and mg, that the backspace invokes help, instead of deleting the previous character. Backspace is also used to page up and back in Info, the Emacs built-in documentation system. On local FreeBSD, backspace does not work in Info. It instead tires to invoke help recursively. Alt-V to scroll up still works, like in manpages.

This problem does not show up in Emacs or mg running on remote FreeBSD when SSH'ing from a non-FreeBSD client laptop. Both editors function properly there. The problem manifests locally on FreeBSD, and on any remote server when SSH'ing from FreeBSD, and even in a web console view of a cloud VPS running FreeBSD, even from OpenBSD or Linux locally.

I found the workaround in the Emacs documentation is to rebind Ctrl-H from the help command to the backspace command.
https://www.gnu.org/software/emacs/manual/html_node/efaq/Backspace-invokes-help.html

In ~/.mg:
global-set-key "\^h" delete-backward-char

In ~/.emacs.d/init.el:
(keyboard-translate ?\C-h ?\C-?)

This means I can no longer invoke Emacs help using Ctrl-H. I would have to type "Meta-X help" aka "Alt-X help" to bring up help. It's reasonable to apply this fix to Emacs and mg locally on my FreeBSD laptop.

But to apply that also on all my remote non-FreeBSD servers, in case I SSH to them from FreeBSD, that seems a bit excessive, or excessive to not modify them and only SSH to them from non-FreeBSD clients.

I included additional findings on stty erase and erase2 related to this in my email below from last year.

Do I have sufficient detail at this point to file a bug report about changing the default way FreeBSD handles Backspace to Ctrl-H?

I also regularly use vi, ee, and neovim.

Let me know and thanks for the great show!
