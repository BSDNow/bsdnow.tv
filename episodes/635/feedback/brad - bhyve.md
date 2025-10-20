Hello, BSDNow family!

It's been a while... I have a bhyve question. I have been digging around the internet trying to teach myself bhyve. I have been looking for/at docs on the interwebs. I wish I could have made it to EuroBSDcon and gone to Benedict and Jason's class. 

So here is my use case. I plan to convert my perimeter firewall from pfSense to OPNsense. Basically, what I am trying to do is to temporarily stand up an OPNsense instance, with three interfaces, in bhyve. The purpose of this vm is to convert the configuration of pfsense to opnsense, since netgate has apparently obfuscated the configs so that they have to be converted by hand. Once I am comfortable that the config will work on actual hardware, I will save said config, and upgrade my existing firewall to opnsense.

So I have a Lenovo mini-server that has FreeBSD 14 and bhyve installed, alas with a single physical interface. So reading docs on the internet, some sources say to use 

ifconfig bridge create

and "addm" the actual interface

ifconfig bridge0 addm em0

However other sources say to use vm switch, like so:

vm switch create public 
vm switch add public em0

So my first question is whether these are the same, and which is better? Related question, as I said, I have but a single interface on the bhyve server. The firewall, in operation, will have 3. So would the right course be to 

vm switch create lan
vm switch add lan em0
vm switch create inet
vm switch create dmz

with no associated interfaces? I then install opnsense and create the three interfaces, one on each switch?

Thanks,
--b
