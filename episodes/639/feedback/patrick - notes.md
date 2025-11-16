patrick

Hi folks,

first a quick note to Tom:

A device making forwarding decisions based on layer 3 information is a router.
A device making forwarding decisions based on layer 2 information is a bridge.
A "switch" is a marketing term that can mean anything but frequently is meant as "faster than competitor X".

-- Radia Perlman - not a literal quote, but from my memory


But my main point is: you can get at least wear/TBW data from NVMe
SSDs with smartctl. Just do

-----
smartctl -x /dev/nvme0
-----

and look for e.g. the "Percentage Used" value.

I use this script to extract wear information from all SSDs in my systems
and hand them over to InfluxDB for later consumption by Grafana.

-----
freenas# cat ssd-wear.sh 
#! /bin/sh

PREFIX='servers.'
SMARTCTL='/usr/local/sbin/smartctl -x'

time=$(/bin/date +%s)
hostname=$(/bin/hostname | /usr/bin/tr '.' '_')
drives=$(/bin/ls /dev | /usr/bin/egrep '^(a?da|nvme)[0-9]+$')

for drive in ${drives}
do
    case ${drive} in
        nvme*)
            wear=$(${SMARTCTL} /dev/${drive} | awk '/Percentage Used:/ { printf "%d", $3 }')
        ;;

        da*|ada*)
            wear=$(${SMARTCTL} /dev/${drive} | awk '/Percentage Used Endurance Indicator/ { printf "%d", $4 }')
        ;;
    esac

    # catch the case that $drive is not an SSD ...
    if [ "x${wear}" != 'x' ]
    then
        echo "${PREFIX}${hostname}.diskwear.${drive}.wear-percent ${wear} ${time}"
    fi
done
