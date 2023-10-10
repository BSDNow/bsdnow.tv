
A question on episode 520 asked about cross-compiling a kernel module from
source with a TARGET_ARCH=armv7.  Here are a couple of options one could
use:

1) Build the module as part of a kernel build making use of the
   LOCAL_MODULES stuff.  By default make buildkernel will look
   in /usr/local/sys/modules.  Any files or sub-directories listed
   there will be treated as a directory that builds kernel
   modules.  For example, I use this to build drm-kmod as part of
   my native buildkernel on my laptop by cloning the drm-kmod
   git repository into my home directory and then creating a
   symlink from /usr/local/sys/modules/drm-kmod to my git clone.

   So one option is that you could create a symlink
   /usr/local/sys/modules/foo that points to your desired kernel
   module source directory.  Then any make buildkernel/installkernel
   invocations (including cross-builds) will pick it up.

   However, if you don't want to build the module on your host
   system, only for your cross-builds, then you can set
   LOCAL_MODULES_DIR to override the default of /usr/local/sys/modules.
   The only trick is that the build will assume every file under
   whatever alternate directory you want to use is a kernel module
   source directory, so you need a "clean" directory that only contains
   kernel module build dirs (or symlinks to kernel module build dirs).

   For example, you could create /path/to/modules as an empty
   directory, then store the build directory as a subdirectory
   in that:

   mkdir /path/to/modules
   cd /path/to/modules
   git clone ...../mymodule.git

   Then make buildkernel TARGET_ARCH=armv7 LOCAL_MODULES_DIR=/path/to/modules
   will build 'mymodule', and installkernel will install it.

2) Build the module standalone.  This one is a bit trickier, but
   doable.  This is easiest if you have the result of 'make installworld'
   handy (what you would pass to DESTDIR for installworld/installkernel).

   For this case, you want to tell the compiler you are cross-compiling
   explicitly via '-target' and you want to tell it where to find its
   headers via '-sysroot'.  You will also probably want to tell the build
   system that you are using a different architecture and where the kernel
   source tree is located.  This will be a bit different though as you
   won't set TARGET* but MACHINE* directly.  This is untested, but assuming
   you have installed your world previously to /arm/world and that your
   source tree is at /arm/src I think you could do something like this in
   your kernel module build directory:

   make MACHINE_ARCH=armv7 MACHINE=arm MACHINE_CPUARCH=arm SYSDIR=/arm/src/sys
  	CC="cc -target armv7-freebsd-gnueabihf --sysroot /arm/world"

   It may be that for the kernel module build the --sysroot isn't needed.
      To build a user program that uses bsd.prog.mk, you would use the above
   command line, but without SYSDIR (and it would need the --sysroot for
   sure).  For cross-building user programs I usually just leave the
   MACHINE* bits off and just set CC as that's often good enough, but
   kernel modules probably have enough machine-specific CFLAGS that you
   probably do need MACHINE* for a kernel module.

-- 
John Baldwin 
