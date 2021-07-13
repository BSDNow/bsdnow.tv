Hi All,

I am a new semi convert from Linux to FreeBSD. Recently, I bought a used Dell laptop as my daily driver and dual booted it with Debian KDE and FreeBSD KDE. Although the FreeBSD install was semi painless, I still am having several minor issues. 

1.  I have searched the BSD manual and inquired to several sources to print to my home network computer without success. It has a static IP address and every other device (cell phone, tablet, and laptop) can print wirelessly to it including the Debian KDE install except from the FreeBSD install.  It is an older one Brother MFC495CW. I am not sure if I should be using CUPS, LPR, or something else.

2. I am still slightly confused if I am updating correctly after listening to one of your podcasts. After installing, I was able to upgrade to version 12.2. I am not a bleeding edge type person and will upgrade to version 13 in the future but not now. To update the system from the terminal (because I have not explored a bash type script yet) I do the following:

sudo freebsd-update fetch install
sudo pkg update
sudo pkg upgrade

I am avoiding ports and other things, etc until I understand them better.  Is this correct? Also, I will use the terminal command that I used to upgrade to 13 from 12.2 that I used to go from 12.1 to 12.2 in the future.

3. Because there is no pathway to install my favorite browser Vivaldi, I installed the Iridium browser. Each time I open it, it asks if I want to set it as default. I have checked settings in the browser and system setting and cannot locate where to set it as default. Any clue? Firefox is also installed. 

Last, after years of exploring desktop environments, I have settled on KDE plasma. FreeBSD is not the most up-to-date operating system, but I am exploring an alternate to Kubuntu with my custom system updater script that I install on others computers as an alternate to Windows. If I can find a decent KDE script to install for FreeBSD along with an easy way to create a one button updater like I have on Linux, I will seriously consider FreeBSD as an alternative for future installs instead of Debian KDE.

Thank you in advance for your help and suggestions.

Jim
