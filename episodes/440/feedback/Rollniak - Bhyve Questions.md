Hello everyone,

Thanks for your show, I discovered the BSD-like world with you some years ago. I'm grateful for that !

I use FreeBSD as a workstation in daily basis. I take the sysadmin role in some small open-source project.
One of these projects run Proxmox Virtual Environment (ProxVE) and I hoped it will work in a Bhyve VM like this:

.---------------------------.
| KVM Virtual machine Guest |
'---------------------------' ^
.---------------------------. |
|         Bhyve VM          | |
|    Proxmox VE as guest    | |
'---------------------------' |
.---------------------------. |
|    FreeBSD Workstation    | |
|        Bhyve Host         |
'---------------------------'

But I got this message in the VM instead:

```
No support for KVM Visualization detected.
Check BIOS Setting for Intel VT / AMD-V / SVM.
```

The main goal is to have a quick testing environment on my workstation and make some Proof of Concepts.

So, here my questions:
- Does Bhyve support nested virtualisation ?
- If yes how to configure FreeBSD/Bhyve in order to make KVM virtual machines works inside a Bhyve VM ?
- If not, can someone explain why ? 

Have a nice day, and keep going ! :D
Rollniak.
