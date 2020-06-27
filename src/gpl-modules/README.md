Broadcom OpenNSA kernel modules
===============================

Broadcom's original build system for OpenNSA is baroque and broken beyond the
point of trying to fix it. As such, there is now a Kbuild-based build system
that builds all Linux kernel modules from OpenNSA in a strightforward and
idiomatic fashion.

We had to rename some modules around as there were some naming collision with
source code files. A list of modules, their (presumed) purpose, and original
names is available below.

To build against a Linux source tree, run:

    make -C path/to/linux M=path/to/OpenNSA/src/gpl-modules/ BCMSDK=path/to/OpenNSA modules

You'll then have a bunch of .ko's lying around. You can use `modules_install`
to install them into a module directory (by default into `/lib`, but that can
be overriden by setting `INSTALL_MOD_PATH`).

Modules
-------

 - **bcm-kernel-bde**: Broadcom Device Enumeration core kernel module (originally called `linux-kernel-bde`)
 - **bcm-user-bde**: BDE 'user helper' (originally called `linux-user-bde`)
 - **bcm-knet-mod**: Linux network driver for XGS switch devices (originally called `bcm-knet`)
 - **bcm-knet-cb**: Test driver fo rcall-back fucntion in `bcm-knet-mod` (originally called `knet-cb`)

