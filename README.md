Pairman's Linux From Scratch Distribution 11.3 x86_64 20230529 version, supporting only Surface Pro 7+.

Added many packages and features in addition to the LFS and BLFS book, mainly including UEFI support, microcode for CPU, GPU and WLAN, modifications of multiple scripts, ```mimalloc``` as the default malloc() library.

**This OS is intended to be used only as a toy for educational purposes, configuring and flashing is NOT recommended**. Files' copyright belongs to their original owners.

The split files generated by ```split -b 25M input.tar.xz output.tar.xz.part``` can be retrieved using ```cat input.tar.bz2.part* > output.tar.gz```. You need at least 1) modify ```/boot/grub/grub.cfg``` and regenerate the EFI files under ```/boot/efi```, 3) recofigure and recompile the kernel in ```/opt/linux-6.1.11``` with customized drivers/microcodes and 4) reconfigure the scripts in ```/etc/init.d```, ```/etc/udev``` and ```/etc/sysconfig``` to make it bootable.
