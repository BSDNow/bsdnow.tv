I have lost a whole work day trying to figure this out. How much time did you lose trying to connect to an OPEN NON-encrypted Public WiFi Network?  when your /etc/rc.conf line  is  ifconfig_wlan0="WPA DHCP"

I have lost a whole work day trying to figure this out. How much time did you lose trying to connect to an OPEN NON-encrypted Public WiFi Network? 
    https://forums.FreeBSD.org/threads/wlan-associated-but-dhcp-not-working-iwm-iwlwifi.88343/post-603623​https://forums.FreeBSD.org/threads/wlan-associated-but-dhcp-not-working-iwm-iwlwifi.88343/post-603623​​​ifconfig_wlan0="WPA DHCP" for a encrypted WPA-PSK network

    ifconfig_wlan0="DHCP" for a non-encrypted OPEN network

The WPA_SUPPLICANT will not connect to an open nonencrypted network if your leave text string "WPA" in the file /etc/rc.conf line  ifconfig_wlan0="DHCP"

This is a problem for connecting from FreeBSD using a WPA-PSK wifi access point setup normally for company or home and then go on a trip and try to connect to a HOTEL or McDonalds or BurgerKing wifi network Access Point that is open and non-encrypted.   WPA_Supplicant command should silently figure out to drop "WPA"  because you selected to connect to an open network. At least it should ASK "Are you sure you meant to connect to an OPEN nonencrypted network SSID "Hotel_Rapunzel".  Or give a loud razzle audio error,  ERRRCH connecting to an Open Network,  ERRRCH" in Toucan Sams voice.   Ok, at least mention the error in dmesg,  Okay?    I have lost a whole work day trying to figure this out. How much time did you lose trying to connect to an OPEN NON-encrypted Public WiFi Network?   Your Mind's eye and repetitive use of, "I always put in the text string  "WPA"  It has to be there or the connection does not work with normal WPA-PSK encrypted Wifi Access Points.  You forget, Oh, this hotel network is "OPEN BABY OPEN" and I Shant use "WPA"  with my "DCHP" to get a connection.     Let the gurus who go out on conferences figure out a solution.   Send a note to  BSDNOW.TV show  Developers listen to their content.

    https://srobb.net/fbsdquickwireless.html SRobb freebsd quick wireless setup


    For Open non-encrypted network minimal entry

    [CODE=none]network={

    ssid="innflux"


    key_mgmt=NONE

    }[/CODE]For a WPA-PSK encrypted network, bare minimum setup of 3 lines and 1 comment

    [CODE=none]network={

    #: my NetGear box

    ssid="NETGEAR59"

    psk="my_passkey_892"

    key_mgmt=WPA-PSK

    }[/CODE]


See  https://forums.FreeBSD.org/threads/wlan-associated-but-dhcp-not-working-iwm-iwlwifi.88343/post-603623  for details

https://forums.FreeBSD.org/threads/wifi-stopped-working-13-1.85429/post-603627

https://github.com/ghostbsd/networkmgr/issues/85

I felt that you might like to explain in your witty banter this during your questions section.   For an answer read the code, the manual, and ask your local developer of "wpa_supplicant" code, why the end user has to be so knowledgable as to be a UNIX GURU and know by heart, OPEN Networks don't use "WPA" to make a wifi connecting exactly because it is "OPEN"  dummy.  See that is how it is suppose to work and how the rules are plainly clear.  Use "DHCP" or open nonencrypted networks.  Use "WPA DHCP" for WPA-PSK encrypted networks.  This is very logical and follows the rules.  You can understand now, correct?

goes off stage mumbling about windows and mac make it easy for the end user.  To use FreeBSD you must attain UNIX GURU status or be a knowledgeable system administrator.   GhostBSD.org and NetworkMgr application get you there 90% of the way towards usability.

Better Wifi enable posts
https://forums.ghostbsd.org/viewtopic.php?f=64&t=570  PCI  RTL8188ce device
https://forums.ghostbsd.org/viewtopic.php?f=64&t=526  USB RTWN Edimax EW-7811un version 1 and maybe version 2 now,  USB Wifi dongle setup   Manual Wifi Connection step by step

Have fun, pick and choose what you say, enjoy making a light hearted point about end user usability with Wifi connections on FreeBSD.  I think app NetworkMgr for FreeBSD, DragonFly, and GhostBSD, makes them better BSDs on the desktop for wifi connetions.
