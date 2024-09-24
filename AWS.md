# AWS

## Why physical hardware and not AWS?
Initial research concluded that it was difficult to get Gentoo running on AWS. Available guides were complicated and included using an existing AMI and overwritting it with Gentoo data. This did not feel like a good solution, only a hack. It gave up many of the niceities of Gentoo including being able to adjust the system 'offline' in a chroot environment or 'locally' with qemu.

## Personal attempt at AWS

QEMU is very nice for creatng and running VMs locally. Gentoo has a small guide for creating a bootable image that can run on qemu [Gentoo QEMU Guide](https://wiki.gentoo.org/wiki/QEMU)


The basic steps are:
1. Create an image
2. Mount image to a looback device
3. partition the image
4. Create a filesystem
5. Install Grub

At this point you have a bootable image, but the image is empty.

You can now mount the root partition of the loopback device to a local folder and install Gentoo stage-3 via the handbook proceedure [Gentoo Handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Stage)

Things to remember when doing install:
1. Enable ssh at the default runlevel otherwise you won't be able to connect to the instance. Features such as serial connect unfortunately won't work on the custom image
2. set root password
3. Create a user so you can log in 

The ability to chroot into the locally mounted image is a nice feature of Gentoo because it does not require you to 'start' the image in a VM runtime or emulator (as long as your desktop is the same CPU architecture as the image). 


## Testing image in QEMU

Once installation via the handbook Try out the image in QEMU to make sure it starts and boots up. I had some issues getting the externally install grub to work. To fix this, in the grub rescue shell I was able to

```
ls
```

to find the drives available


```
ls (hd0,1)
```

showed me the root partition, so I set that as root:

```
set root=(hd0,1)
```

then I could start up the kernel

```
linux /boot/vmlinuz... root=/dev/vda1
initrd /boot/initramfs...
boot
```

Once the machine was booted I re-installed grub via `grub-install` and everything worked going forward.

## Image format

AWS only supports a few image formats. I do not know which is the best but I had success converting my QEMU image to a 'streamOptimized' VMDK.

```
qemu-img convert -O vmdk -o subformat=streamOptimized gentoo-ami.img gentoo-ami.so.vmdk
```


## Uploading Image

First, upload the image to an S3 bucket. 

This guide had helpful information about setting the proper policies and creating a 'container.json' file: [AWS Custom Image Guide](https://dev.to/otomato_io/from-iso-to-ami-how-to-create-your-own-custom-ami-5213)

Rather than running 'import-image' as described above, run 'import-snapshot'. 'import-image' does some checking on kernel version and injects drivers into the image to make sure it runs on AWS. Our custom image is not expected by the importer and will fail. These checks are not run in 'import-snapshot'.

Once the snapshot is imported you can create the 'image' via the AWS console. Make sure you selected the correct 'boot-mode'. This depends on how you installed grub. If you told it to use legacy bios, chose legacy-bios. If using EFI, choose that option.



