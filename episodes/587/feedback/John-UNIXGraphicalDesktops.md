The uncertain possible futures of Unix graphical desktops

UToronto's Chris Siebenmann was too cynical.
KDE Plasma and Wayland run under FreeBSD current:

# pkg install drm-kmod wayland plasma6-plasma xorg-fonts alacritty seatd dbus

kldload your GPU's DRM module, in my case
# kldload i915kms

add your user to the video group
# pw groupmod video -m user

start dbus and seatd
# service dbus onestart
# service seatd onestart

and start Wayland,
user$ dbus-launch ck-launch-session startplasma-wayland

PS thank you for the wonderful interviews from EuroBSDcon.
Guessing they took you away from tech sessions, hallway track
conversations and socializing, but they were interesting
dialogues and powerful advertisements for BSD conferences.
More BSD Now interviews, please!
John
