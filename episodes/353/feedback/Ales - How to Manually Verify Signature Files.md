Hi Allan, Benedict and JT,

Thank you very much for the great podcast. After using Linux for many years thanks to OPNsense I recently I discovered BSD world and it's really exciting ;-)

Would you be so kind and help me answer one "pkg" question?

I have one OPNsense box that can't have internet access and I needed to install os-wireguard plugin on it. I managed to do it by fetching os-wireguard plugin and all dependencies on a different internet connected OPNsense box and installing it over shell on the offline box.

The only thing I don't know / doesn't work is when I tried to check signature of those "pkg" packages on my Linux box.

I tried this:

sha256sum bash-5.0.11-91239e0a88.txz | tr -d '\n' | sed -E 's| +.*||' | openssl dgst -verify OPNsense-20.1.pub -signature bash.txz.sig

and

openssl dgst -verify OPNsense-20.1.pub -signature bash.txz.sig <<< '1947d09134fc7478f81a6ca1709a55962cfb8ce4d911289b6e9466871bbed8ef'

on packages and sig files that I download from: https://pkg.opnsense.org/FreeBSD:11:amd64/20.1/MINT/20.1.2/OpenSSL/Latest/ to verify that the fetched files on my USB stick were not replaced by something I don't want.

Based on my research this should work but I always get Verification Failure message.

Could you please help?