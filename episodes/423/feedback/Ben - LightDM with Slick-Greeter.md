Hi Allan, Benedict, JT, Tom,

Not a question - more of an information share if I may.

For the light weight FreeBSD desktop, people typically want to choose a display manager not linked to GNOME or KDE so they can have a graphical login screen without pulling in large numbers of dependencies.

Traditionally, x11/slim has been popular… and whilst it still works it hasn’t seen any new releases since 2014.

I wanted to make people aware of an alternative that is still in development and quite pleasing to the eye: x11/lightdm and x11/slick-greeter. LightDM provides the backend login / session services, whilst Slick Greeter provides the graphical front end (aka greeter).

We recently made a change to the x11/slick-greeter port so that it automatically modifies the lightdm.conf file to set slick greeter as the configured greeter when the package is installed (as long as the lightdm.conf setting is still the default value which is commented out). This change hasn’t yet made it into the quarterly ports branch.

For those that want to give it a try, it’s as simple as running the following from a console (install your graphics drivers and desktop environment separately):
# pkg install slick-greeter
# service lightdm enable
# service lightdm start

Thanks to madpilot@ and ericbsd@ (of GhostBSD fame) for their work in helping maintain these ports.

Regards,
Ben