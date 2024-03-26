
# Chroot
Chroot (change root) allows one to change the apparent root directory of
the shell. This is handy if you want to effectively have multiple linux
'systems' and change between them.

For example, in my /home/james folder I could have a directory named gentoo1.
Issuing the command chroot /home/james/gentoo1 moves the shell to that directory, but the new directory will appear to be the root of the system now.

The chroot command can even be used in conjunction with QEMU (machine emulator)
to create a 'system' for a different architecture.

# Build Server
The ARM SOC's are quite slow. Compiling the gentoo system from scratch could take days. It would be preferable to compile on a faster system such as my x86_64 desktop. Cross compiling is an option, but many packages have implicit dependencies on the system environment and fail to cross compile. An alternative is to use an emulator like QEMU.

To start, I unpacked the standard aarch64 stage3 tarball from the Gentoo website into a directory on my desktop and [configured QEMU](https://wiki.gentoo.org/wiki/Embedded_Handbook/General/Compiling_with_QEMU_user_chroot). I can now simply chroot into this new system via QEMU and build any system packages for the aarch architecture using standard portage commands. Portage has the ability to make binary packages, so I can compile all packages on my fast x86 machine and install them on the ARM boards as binary packages. I can even set custom compile flags that will be picked up by all packages, ex:

```
-march=armv8.2-a+crypto+fp16+rcpc+dotprod
```

