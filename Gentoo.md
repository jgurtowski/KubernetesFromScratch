# Gentoo
![GentooLogo](images/gentoologo.svg)
[https://www.gentoo.org](https://www.gentoo.org)

# Gentoo Linux Summary
Gentoo is a linux distribution focused on customization. Contrary to many other distributions which precompile packages for users, Gentoo's packages manager (Portage) pulls down package sources and compiles them on your computer. A few touted benefits of compiling from source are:

1. Only compile features you need.
   Precompiled distributions need to support the general use case for most users which means most packages are built with the majority of options turned on. For instance ffmpeg supports many codecs for both video and audio. It also has flags for various CPU instructions as well as GPU acceleration. In addition it supports various streaming and storage integrations such as samba. A binary package builder does not know which of these features a user will use so must compile most if not all of them into the package including their dependencies. One quickly finds that one package (ffmpeg) could pull in a ton of dependencies when all of its features are enabled. Gentoo allows the user to customize which flags/dependencies are need for their use case vie 'USE' flags and only installs those.
   
2. Packages can be optimized for the architecture/instruction set of your machine
   When a package is compiled, many optimizations can be done by the C/C++ compiler to tune the software for the specific chip running the machine. Binary packages provided by other distributions are typically compiled with fewer optimizations because they have to run on a vast array of x86_64 machine. That includes old machines from 20+ years ago. By compiling the packages on the machine they will run, the compiler is free to optimize as much as possible and make use of new instructions present in today's chips. This in theory can produce programs that run faster.

3. Rolling release
   Other linux distributions have 'Releases'. These releases lock certain package versions and provide stable platform to build packages that operate higher in user space. For commercial linux distros that provide users support, this can be beneficial because it reduces the surface are the team must support. On the downside, system packages tend to be quite old. Anyone who has used an enterprise linux distro will see commonly used packages such as python will be quite old. Solutions to this typically come in userspace where, in essence, another package manager in userspace is used to provide the user with up to date software.

4. Slots
Gentoo allows multiple versions of package to be installed on a system at the same time. This can be helpful for tools such as python or Java where you may have an application that requires an older (or newer) version of python than what is installed as the system default. Gentoo has a utility called eselect which allows easy switching between different versions of tool.

```
eselect java-vm set openjdk-bin-11
```

This is great when you need to run some old software. However, there is a downside. The system packages still rely on a specific version of these base packages (java, python etc). There are so many dependencies that rely on these tools across the system, there is no way they can build all of these packages with each version of these tools (java, python etc). Switching back and forth between versions of these packages for every application is messy and error prone.  A better solution to this is the virtual environments created by languages like python, where the application has its own version of the language and packages which are different from the system. A more generic solution is docker which can package an entire system of depenencies if necessary and does not affect the system versions of packages.


# Why Gentoo?

Above are some of the 'selling' points of Gentoo and make it different from other linux distributions. However, these were not the reasons I chose Gentoo for this project. I simply chose Gentoo because it is the distribution with which I am most familiar. 
