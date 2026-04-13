Hi All,


Thanks for producing the show, I like the breadth of topics that it covers.  I'm writing in response to a comment that Jason made regarding wishing that FreeBSD could natively run Flatpak images.  I ran across an article that discusses creating immutable Linux images using bootc and OSTree.   Here's a link to the article:  <https://a-cup-of.coffee/blog/ostree-bootc/>

It turns out that OSTree uses podman to create a bootable OCI image of a Linux installation.  The article even has a "Deploying a bootc image" that shows the required steps.   It also contains a link to an issue that was raised to get OSTree images working on other Linux distros:  <https://github.com/bootc-dev/bootc/issues/865>

 Since FreeBSD has a native podman  port now, I was wondering whether this new method brings FreeBSD closer to being able to run a bootable OCI image of a Linux installation.  From my perspective,  it seems less kludgy than running a Linux jail.


Regards,
Tim
