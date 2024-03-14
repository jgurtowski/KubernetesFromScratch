
# Cross Compiling - Just use emulation
Gentoo has a nicely packaged toolchain for cross compiling. The cross compiler can
even be plugged into portage relatively easily to build packages for other systems.
This works well for 90% of packages however there are some packages that have environmental
assumptions built in and make it difficult to build them with a cross compiler.

The alternative is to use an emulator like QEMU which allows for CPU or entire system emulation.
The downside of emulation is it is much slower than cross compiling. The advantage is that it
can emulate the entire system so you are essentially building a separate system in a chroot for a
different architecture. For architectures like aarch64, which is well supported by gentoo, packages
rarely fail to build.

Although on a percentage basis emulation may be drastically slower, I found that on a modern
i7 CPU, the nominal difference was not worth the inconvenience of cross compilation and debugging.



# Writing apps in C/C++ is pretty portable
- Languages like Java and Python are touted for being portable, but they are heavy weight, requiring a runtime. The runtime is always being updated and causes compatibility issues.
- Static C binaries can be hard to build (dependencies) but they are easy to deploy
