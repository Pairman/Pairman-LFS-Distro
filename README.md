Pairman's Linux From Scratch Distribution 11.3 x86_64, supporting only Surface Pro 7+.

Added many packages and features in addition to the LFS and BLFS book, mainly including UEFI support, microcode for CPU, GPU and WLAN, modifications of multiple scripts, ```mimalloc``` as the default malloc() library.

**This OS is intended to be used only as a toy for educational purposes, configuring and flashing is NOT recommended. Your warranty is now void. You have been warned. Use at your own risk. Files' copyright belongs to their original owners.**

It should be extracted under ```/mnt/distro```, with a root partition mounted at ```/mnt/distro``` and a standalone efi partition mounted at ```/mnt/distro/boot/efi``` on the host system. You need at least 1) modify ```boot/grub/grub.cfg``` and regenerate the EFI files under ```boot/efi```, 3) recofigure and recompile the kernel with customized drivers/microcodes and 4) reconfigure the scripts in ```etc/init.d```, ```etc/udev``` and ```etc/sysconfig``` to make it bootable on other devices. Root password is ```root```.


Hints on setting up host chroot:
```
# SET UP LFS
export LFS="/mnt/distro"
alias mountlfs="mount -v --bind /dev $LFS/dev; mount -v --bind /dev/pts $LFS/dev/pts; mount -t tmpfs -o nosuid,nodev tmpfs $LFS/dev/shm; mount -vt proc proc $LFS/proc; mount -vt sysfs sysfs $LFS/sys; mount -vt tmpfs tmpfs $LFS/run; mount -B /sys/firmware/efi/efivars $LFS/sys/firmware/efi/efivars"
alias umountlfs="mountpoint -q $LFS/dev/shm;umount $LFS/{dev/shm,dev/pts,sys/firmware/efi/efivars}; umount $LFS/{sys,proc,run,dev}"
alias chrootlfs="chroot /mnt/distro /usr/bin/env -i HOME=/root TERM=xterm-256color PS1='(chrootlfs) \u:\w$ ' PATH=/usr/bin:/usr/sbin /bin/bash --login"
```
