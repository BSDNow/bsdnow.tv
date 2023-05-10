Hi, guys,

Great episode as always. Glad to hear more people discovering the tilde-escapes in ssh, a feature inherited from rsh at the dawn of network time.  A time when specifically hopping from host to host was was more common, because each host had unique local resources.

No one can doubt the utility of tilde-period to close your connection, but there are two more escapes that are useful way more often. One was mentioned, tilde-hash. It’s most useful for seeing why ssh won’t exit after exiting the shell. A forwarded connection, like an X client, prevents ssh from exiting. You can solve the problem with tilde-ampersand which puts ssh in the background until the tunneled/forwarded client closes its connection.

The other escape is tilde-control-z or tilde followed by whatever is set to send SIGSTOP from the terminal. This lets you suspend your ssh connection, run some local commands, then return to your suspended connection by typing “fg”. This is invaluable when you’re in a situation where you cannot open another terminal and don’t have access to tmux or screen. Think connections through a jump/bastion host or a serial connection.

Maybe I’m old, but I still use tilde-SIGSTOP almost every day. It’s great for the forgetful who connect to a host and then realize they forgot to scp a file first. Kind of like getting you your car, and then needing to go back inside for your keys. 😉

Adrian
