



Hello @everyone in the BSDNow Team.

Over a year ago, I started using FreeBSD as the main operating system in my Homelab and recently try to automate more and more things, mainly setting up FreeBSD VMs.

After using FreeBSD VMs for the longest time, I decided to try jails because they need much less resources and offer better privilege insulation.

I read a lot about jails online and in books (Absolute FreeBSD and FreeBSD Mastery: Jails by Michael W. Lucas were really helpful) and decided to only use jails going forward.

At the same time, I started to convert my manual installation steps from my notes into Ansible Playbooks, which made it much easier to manage all of my VMs and services.

When I was looking for ways to set up services in FreeBSD jails with Ansible, I came across a talk that Benedict gave about the management of FreeBSD with Ansible in 2017. If I can remember correctly, he also mentioned Jails in the same context, but didn't go into much depth.

Nevertheless, are there any tips and tricks that you can give me on how one can best manage FreeBSD jails with Ansible? (Setting up rc.conf, install software and SSH keys, create users, etc.).

Anyway, thanks for the show, keep it up.


