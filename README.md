## brcm-arm-toolchains

This is a toolchain for building router firmware based on Broadcom Cortex-A9. Example products are ASUS RT-AC56U,  RT-AC68U, RT-AC87U and RT-AC3200 etc. This toolchain is compiled from buildroot source codes published in ASUS GPL codes. Major components in this toolchain include:
* GCC 4.5.3
* uClibc 0.9.33.2
* Linux kernel 2.6.36.4

Essentially the same used by Asus to build their latest ARM based ASUSWRT or by other people to build Asuswrt-Merlin. ASUS's toolchain in their GPL code uses uClibc 0.9.32.1 and compiled in an ancient version of LinuxThread thread library i.e. with NPTL disabled. What's new in this toolchain is uClibc 0.9.33.2. It's the latest stable release of uClibc which supports Native Posix Thread Library. NPTL is enabled as well as TLS in both libc and gcc.

The toolchain has been tested to successfully build Asuswrt-Merlin v378.55. And of course it also runs on the target board, RT-AC56U. 

Although this toolchain is created primarily to build ASUSWRT or its variants. I believe it's not the only application. If people have success stories using this toolchain. I'm happy to hear from you.

### Setup for building ASUSWRT or Asuswrt-Merlin

This toolchain is a drop-in replacement for the toolchain included in ASUS GPL code and Asuswrt-Merlin. For first time builders, you go to `src-rt-6.x.4708/toolchains`, rename the existing `hndtools-arm-linux-2.6.36-uclibc-4.5.3` to a different name. Then create a symbolic link with the same name linking to the `hndtools-arm-linux-2.6.36-uclibc-4.5.3` that you check out from this repository.

### Known issue

One program, `wred` does not run properly. It's a userland middle-ware, part of the DPI software stack from Trend Micro that ASUS includes in newer models of their routers. The fix perhaps is only for Trend Micro to tidy up their use of pthread APIs in `wred`.

### Source code

The source code is "buildroot-2012.02" which is available from published ASUS GPL codes.

### Forum discussion

http://www.snbforums.com/threads/arm-toolchains-with-nptl-for-asuswrt-merlin.27938/
