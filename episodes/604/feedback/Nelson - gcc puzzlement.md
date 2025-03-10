Comments in the latest episode of BSD Now indicate
puzzlement over the status of gcc support for Ada.
The issue is that two decades ago, about gcc-4 or
so, parts of the gcc compiler for Ada were written in Ada itself.  This meant that you need an earlier version of gcc to build the newer compiler, and the bootstrap problem exists ever after.  This has also happened more recently with support for the D language.  If O/S distributions always
supplied all languages that gcc supports, this would not be an issue.  However, some major distributions fail to do that, among them CentOS GNU/Linux and some members of the BSD family.  FreeBSD 15 has a package, gcc6-aux-20180516_3,1, that provides Ada, but is is 9 major compiler generations behind, making it a difficult job to bootstrap Ada support for modern compiler versions.  Modula-2 (gm2) has been supported
by gcc for a few years now, but many distributions fail to supply it.  At Utah, I routinely build new gcc releases every few weeks on our major servers, and my goal is always to include every compiler that gcc can produce.

Apple does not supply any gcc compilers, and it has been several years since out-of-the-box gcc releases will build on macOS.  There is some work in this area to fix that problem, but it has not been integrated into the master gcc source tree.
