Hi Guys,
  This is for Jim from the  episode 412.  I'm not familar with KDE but X is X.  You can set the default browser using xdg-utils app called xdg-settings in Freebsd.

```
# To get Vivaldi browser on your FreeBSD machine the easy way
# install git if it is not already installed as root
doas pkg install git
# From your user directory or some directory under it 
git clone https://github.com/mrclksr/linux-browser-installer.git
# Please read all the notes [here](https://github.com/mrclksr/linux-browser-installer) before going further as they tell how to get the linuxulator going
# change directories to linux-browser-installer
cd linux-browser-installer
# run the installer script as root
doas ./linux-browser-installer install vivaldi
# You can also find more information on using the Linuxulator to install your favorite browser and other apps [here](https://forums.freebsd.org/threads/linuxulator-how-to-install-brave-linux-app-on-freebsd-13-0.78879/)
# now for the real magic making your favorite browser the default when you can't find any other way
# install xdg-utils as root
# for more information about [xdg-utils]( https://www.freedesktop.org/wiki/Software/xdg-utils/)
doas pkg install xdg-utils
# check to see which browser is set as default as your normal user
xdg-settings get default-web-browser
# Set the default web browser to your favorite you just need to know the name of it's desktop mime file as your normal user
xdg-settings set default-web-browser vivaldi.desktop
```

I had to use this method since I use a tilling window manager called AwesomeWM however I did find this about [KDE](https://userbase.kde.org/System_Settings/Default_Applications)

Anyway I hope this helps Jim and others.  As always I really enjoyed the episode :)

-- 
  JohnnyK
