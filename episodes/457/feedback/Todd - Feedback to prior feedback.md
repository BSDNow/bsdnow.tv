Hey,

I just heard the latest episode "Compiling 50% faster" and more specifically the question regarding the white macbook. It may be a little late to relay this information, but just in case, here it goes.

I have a 2007 White Macbook that is running NetBSD. There are some quirks to these machines. While, they support EFI, they are a little off. The early ones (for sure the 2007/2006 models) can run 64-bit kernels but boot using 32-bit EFI. This can make for a hassle, so first thing for NomadBSD is to make sure the 32-bit files are present for booting, if not, there are some guides online on how to bake these into images. 

One other tip, the 2007 at least can have it's firmware changed, which lessened a lot of my hassles. It wouldn't boot NetBSD without doing that. So, the 2007, and maybe a few other models share some similar hardware to a Lenovo Thinkpad around that time, the X60/T60. More specifically for this, they share the i945 chipset. No special hardware is required, but the 2006/2007 models can be flashed with Coreboot/Libreboot. Which makes the process of getting systems to boot a whole lot easier.

https://libreboot.org/docs/hardware/macbook21.html

Todd
