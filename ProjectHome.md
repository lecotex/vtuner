## Latest news ##
  * **2013-04-18:** KERNEL DRIVER: RELEASE\_1.4
Optimized internal memory handling.

  * **2013-04-02:** KERNEL DRIVER:
Update for compilation on Linux kernel 3.7.0 or newer.

  * **2012-09-19:** KERNEL DRIVER: RELEASE\_1.3
Updated to work with DVB API 5.5 or newer. Code is compatible with Linux kernel 3.3.0 or newer.

  * **2012-07-30:** KERNEL DRIVER: RELEASE\_1.2P3
Fix for possible memory leakage. Update is recommended!

  * **2012-01-10:** APPS: RELEASE\_2.1
Better server usage on not fully working drivers (see KNOWN ISSUES)

  * **2012-01-04:** APPS: RELEASE\_2
updated almost all binaries to be in sync with latest development: arm, i686, mipsel (including vtuner-client.ipk), ppc, sh4.

  * **2011-10-13:**
added tuner group support, added network protocol versioning. One way backward compatibility built-in (clients can be net-proto-v0)

  * **2011-08-06:**
filtering for tuner type was missing since refactoring the server code, this has been fixed. Only relevant if you share different types of tuners on the same subnet. Compatible with clients from release 20110717-[r1](https://code.google.com/p/vtuner/source/detail?r=1).

  * some bug fixes for the client
  * Source code repository has been migrated to mercurial
  * A kernel modul is now available for hardware other then dreamboxes (DMM)
  * Plugin for client configuration is now available for dreamboxes. No more configuration file hassles.

> [How to use](Usage.md)

> [Big picture scheme](BigPicture.md)

## Known Issues ##

  * **DVB drivers with DVB API not fully implemented:** In [issue#11](https://code.google.com/p/vtuner/issues/detail?id=#11) we have discovered that some DVB drivers are implemented not fully. The callback function .get\_frontend() is there missing what triggers error on ioctl call FE\_GET\_FRONTEND. The workaround for the error was added, but the only solution is to use better drivers (try to update drivers, or change hardware). In the same issue was shown another aproach - emulation the call by reading cached frontend values. But such aproach adds another code complexness what is not what we like so much.

  * **vtunerd.mipsel works only for Dreamboxes:** Regarding [issue#13](https://code.google.com/p/vtuner/issues/detail?id=#13) there is some inconsistence in DVB API between vendor boxes. Original Dreambox API is supported, **but only up to August's 2011 DVB drivers!**. Other boxes (VU+, ET) are not working at all. We are waiting for access to non working boxes to fix it.

If your issue isn't listed here please use our [issue tracker](http://code.google.com/p/vtuner/issues/list) to report one.

## Restriction ##

  * **Removed Linux kernel support for kernel older then 3.3.0:** In kernel 3.3.0 was introduced DVB API version 5.5 which wass the major rewrite of DVB API internals. We decided to not polute source code with tons of 'ifdefs' and removed support for older kernels. We highly recommend to update to supported kernel version, OR update dvb-core subsystem (please ask for help in mailing list if you are not clear about it). The second, but unpreferred way, is to download version 1.2p3 of vtuner device driver (from [Download](http://code.google.com/p/vtuner/downloads/list) section).

## User survey ##

We'd like to know more about you and how you are using this software. [Please participate in the user survey.](https://spreadsheets.google.com/spreadsheet/viewform?hl=en_US&pli=1&formkey=dHRZTklqLWgyMW1fODJPNTA3U2huUHc6MQ#gid=0)
Please note that your data won't be used for any purpose outside the scope of this project.

## Mailing lists/Groups ##

  * **Support (EN):** Please join [vtuner-en-user](http://groups.google.com/group/vtuner-en-user) if you need support. [mail](mailto:vtuner-en-user@googlegroups.com)
  * **Support (DE):** Melde dich bei [vtuner-de-user](http://groups.google.com/group/vtuner-de-user) an für Support auf Deutsch. [mail](mailto:vtuner-de-user@googlegroups.com)
  * **Announcements:** Please join [vtuner-announce](http://groups.google.com/group/vtuner-announce) [mail](mailto:vtuner-announce@googlegroups.com)

Please note that we should have further groups for native language support, volunteers welcome.

## Access the source code ##

The source code is divided into two repositories

**Application:** Contains the companion user land applications, vtunerd and vtunerc. [browse](http://code.google.com/p/vtuner/source/browse?repo=apps) [checkout](http://code.google.com/p/vtuner/source/checkout?repo=apps)

**Linux driver:** Contains the kernel module if you want to use the client on non DMM hardware [browse](http://code.google.com/p/vtuner/source/browse?repo=linux-driver) [checkout](http://code.google.com/p/vtuner/source/checkout?repo=linux-driver)

**Windows driver:** Empty (_We are still searching for win32/BDA developer_)

**Android DVB app:** Empty (_We are still searching for Android developer_)

## Roadmap ##

  * Integrate server into enigma (plugin), prototype is already done
  * Migrate to autotools as build system
  * Design new vtuner network protocol (remove all dependecy on DMM driver structures)

If you like this, feel free: 