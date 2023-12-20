Hi,

I'm a regular listener of your podcast for many years now. I particularly love the pieces of advice around ZFS and the FreeBSD related news.

This time, however, I am seeking advice regarding the FreeBSD releases signing process.

In particular I'm puzzled by the lack of documentation on how to verify the release deliverables:

There is no documentation.
There are no signed checksum files bundled with the images.
Instead you have to downloaded them from the FreeBSD release information page.
However, you are not done yet! Now you need the key that was used to sign the release.

This is a trial and error process, because there is no documentation which key was used to sign the checksum files. OpenPGP will tell you - once you try validate the signature.

Okay, now you know which key to use. However, since the key might not be available at web of trust locations of your choice, you are going to have to hunt for it. Because, naturally, it is not published anywhere you where looking so far. If there was no mention of a key, why should there be a certificate?

So you are moving on:

Clearly, this is an official key, so it's bound to be listed at "Appendix D: OpenPGP Keys" in the handbook, right? You go there, but only to be disappointed.
While some amount of despair starts to creep in, you are following the only remaining trail of breadcrumbs to the "OpenPGP Keys" article on the website (https://docs.freebsd.org/en/articles/pgpkeys/) and the associated PGP keyring file (https://docs.freebsd.org/pgpkeys/pgpkeys.txt).
Once you got past the unreliable download of the article and pgpkeys.txt (maybe this has been fixed in the meantime, but I had to implement a workaround trying to fetch the file multiple times until the download completes),
and you are lucky, you will find the key in there. However, there is no guarantee, and people have been disappointed in the past: https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=222044#c5
At this point you might ask: how is it possible, that the release signing key of a FreeBSD release is not in the FreeBSD keyring?

I'm glad you asked - the answer is as simple as it is disturbing: the FreeBSD project isn't aware of the key at all. And as far as I can tell from past communication (and the lack thereof), neither does it care to be.

The people signing the release are using their own personal keys, and there is no process in place to make sure minimum requirements are met. But you don't have to take my word for it. Just have a look at the signatures for the current production release (13.2), which are signed by a 1024 bit DSA key using SHA-1: https://www.freebsd.org/releases/13.2R/signatures/

Of course I have filed a security incident (https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=274886), but I wouldn't get my hopes up. So far I have been told this isn't going to be fixed for 13.2 (which I find curious, especially since the signed files are not distributed with the images) and that the use of uncontrolled personal keys is intentional for security reasons.

In addition to all of the above, there are no signed checksums for the distribution files (like base.txz, kernel.xz, ...) at all. Which is really odd, because base.txz in particular is very useful and popular to create jails. Right now, the only way to get hold of a verified base.txz is by downloading an installation ISO, validating the ISO and extracting base.txz from it. Except for the current production release, which is signed by a broken key using a broken algorithm.

While people are asking for readily available and easy to follow documentation as well as a reliable release signing process that covers all deliverables for many years already, so far the reactions from the project can only be described as underwhelming (at best). Which is particularly ironic, given the amount of weight "security" receives in the project FAQ: https://docs.freebsd.org/en/books/faq/.

Do you have any pointers on how to proceed from here? I have to say, after so many years of trying, I've almost given up.
