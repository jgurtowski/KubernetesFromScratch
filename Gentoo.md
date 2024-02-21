# Gentoo
![GentooLogo](images/gentoologo.svg)
[https://www.gentoo.org](https://www.gentoo.org)

# Gentoo Linux Summary
Gentoo is a linux distribution focused on customization. Contrary to many other distributions which precompile packages for users, Gentoo's packages manager (Portage) pulls down package sources and compiles them on your computer. A few touted benefits of compiling from source are:

1. Only compile features you need.
   Precompiled distributions need to support the general use case for most users which means most packages are built with the majority of options turned on. For instance ffmpeg supports many codecs for both video and audio. It also has flags for various CPU instructions as well as GPU acceleration. In addition it supports various streaming and storage integrations such as samba. A binary package builder does not know which of these features a user will use so must compile most if not all of them into the package including their dependencies. One quickly finds that one package (ffmpeg) could pull in a ton of dependencies when all of its features are enabled. Gentoo allows the user to customize which flags/dependencies are need for their use case and only installs those.
   
2. Binaries can be optimized for the architecture/instruction set of your machine
   When a package is compiled, many optimizations can be done by the C/C++ compiler to tune the software for the specific chip running the machine. Binary packages must typically be compiled with fewer optimizations because they have to run on a generic x86_64 machine. By compiling the packages on the machine they will run, the compiler is free to optimize as much as possible. 

3. Rolling release
   Other linux distributions have 'Releases'. These releases lock certain package versions and provide stable platform to build packages that operate higher in user space. For commercial linux distros that provide users support, this can be beneficial because it reduces the surface are the team must support. On the downside, system packages tend to be quite old. Anyone who has used an enterprise linux distro will see commonly used packages such as python will be quite old. Solutions to this typically come in userspace where, in essence, another package manager in userspace is used to provide the user with up to date software.


# Why Gentoo?

Gentoo Linux was initially released in 2002 when 


