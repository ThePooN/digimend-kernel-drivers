DIGImend kernel drivers
=======================

This is a collection of graphics tablet drivers for the Linux kernel, produced
and maintained by the DIGImend project. We maintain this package to provide
newer drivers for older kernel versions which don't have them, and to allow
users to test new drivers before we contribute them to the mainline kernel.

This package supersedes the
[huion-driver](https://github.com/DIGImend/huion-driver) package.

Model support is as follows:

    Original                Rebranded as    Status*

       Huion 580                            likely works
             H420           osu!tablet(?)  works
             H610                           works
             H690                           works
             K58                            works
             W58                            likely works
             W58L                           works
             other                          possibly works

     Yiynova MSP19U                         works
             MSP19U+                        works
             MVP22U+                        works
             MVP10U                         works (t)
             MVP10U IPS                     works (t)
             MVP10U HD IPS                  works (t)
             DP10U                          works (t)
             DP10U+                         works (t)

    * "works"           - tested, works
      "likely works"    - not tested, likely works (75% chance)
      "possibly works"  - not tested, possibly works (50% chance)

    (t) concerns only the input part of this display tablet, output (display)
        support is not provided by this package and should be verified
        separately

    (?) the rebranded model is likely the specified original model,
        but wasn't verified to be.
        osu! is a rythmn game on PC and Mac (and also works on Linux with Wine), where you have to click circles in
        rythm to win. Because the needed skill in osu! can be very high on insane beatmaps, some players uses tablets           and the osu!tablet has been created by Huion because osu! players needed a low-cost tablet.

Please send your testing results to DIGImend-devel@lists.sourceforge.net, or
do a pull request with updates.

Installing
----------

Kernel v3.5 or newer is required. Kernel headers or the build tree for the
running kernel are required.

On Debian-derived systems (such as Ubuntu and Mint) headers can be obtained by
installing appropriate version of `linux-headers` package. On Red Hat and
derived distributions the package name is `kernel-headers`.

To build the drivers run `make` in the package's directory.

To install the drivers and the associated rebinding script run `make install`
as root in the package's directory.

Upgrading
---------

If you run a kernel which already has a driver for your tablet with the same
name as the one being installed (including the case of upgrading an
installation of this package), you will need to unload the installed kernel's
driver using the `rmmod` command and then to (re-)plug the tablet in to allow
the driver from this package to take over.

For example, if you run a v3.11 or later kernel, and/or would like to upgrade
the driver for Huion tablets, then after installing this package you will need
to execute `rmmod hid-huion`, and then disconnect and reconnect the tablet to
make it work.

Alternatively, you can simply reboot the machine.

Uninstalling
------------

To uninstall the package execute `make uninstall` in the package source
directory.
