use any DVB tuner elsewhere with your dreambox or linux desktop

Repository has been migrated to mercurial.

### [R87](https://code.google.com/p/vtuner/source/detail?r=87) release note: ###
  * add Plugin for client config
  * **Known limitation:** no information if restart is needed, if in doubt, reboot you box, restarting enigma is not sufficient
  * no protocol change, servers are compatible from [R70](https://code.google.com/p/vtuner/source/detail?r=70) on.

### [R85](https://code.google.com/p/vtuner/source/detail?r=85) release note: ###
  * **client:** server ip can be specified on the command line, it's possible for client and server to be on different subnets now (thanks to dam72 for testing)
  * **vtunerc.i686:** is now available, required kernel patch can be found here: https://patchwork.kernel.org/patch/894212/
  * no protocol change, servers are compatible from [R70](https://code.google.com/p/vtuner/source/detail?r=70) on.

The first parameter can be option -d /where/control/device/sits originally (on dreambox), there is /dev/misc/vtuner0, open source vtunerc.ko is creating /dev/vtunercX, where X=0...max devices. -d is optional, but must be first, if needed

Next command line options are same like before (-s -S2 -t -c ..), but with optional suffix, which allow direct connection to ip,port and tuner group. The mask is like this:
```
 -<dvb_type>[:server_ip[:server_port[:tuner_group]]]
 <dvb_type> = s, S, s2, S2, c or t
 <server_ip> = ip address of server for direct connection
 <server_port> = port number where vtunerd listen for connection
 <tuner_group> = binary mask for tuner group - WARNING: tuner groupping is currently unimplemented
```
### [R71](https://code.google.com/p/vtuner/source/detail?r=71) release note: ###
Fixed a issue with DVB-C tuner capabilites, DVB-C should now work again.
thanks to H2Deetoo, Ghost and Obi for identifying this.
only the client is changed, compatible with servers from [r70](https://code.google.com/p/vtuner/source/detail?r=70) on.

### [R70](https://code.google.com/p/vtuner/source/detail?r=70) release note: ###
fixed the following issue:
http://www.i-have-a-dreambox.com/wbb2/thread.php?postid=1526470#post1526470
Thanks to H2Deetoo for forwarding the fix.
You have to update both, client and server.

### [R69](https://code.google.com/p/vtuner/source/detail?r=69) release note: ###
fixed issue with: error: DMX\_START failed
reported by joergm6 on 10-Mar-2011
only vtunerd.mipsel effected, compatible with client from [r67](https://code.google.com/p/vtuner/source/detail?r=67) on

### [R68](https://code.google.com/p/vtuner/source/detail?r=68) release note: ###
fixed client version numbering

### [R67](https://code.google.com/p/vtuner/source/detail?r=67) release note: ###
Added Support for FE\_SET\_PROPERTY
- not compatible with older versions !
- mipsel server is untested, will not work if image isn't recent


### [R64](https://code.google.com/p/vtuner/source/detail?r=64) release note: ###
**fix client failure if only one mode is given**

Known Issues:
**vtuner is broken with newer images, because of new features in the vtuner API not yet implemented. will be fixed**

NOTE:  clients and server are compatible from version [r58](https://code.google.com/p/vtuner/source/detail?r=58) on

### [R63](https://code.google.com/p/vtuner/source/detail?r=63) release note: ###
OE1.6 build did not work with DM7025 (no OE1.6 available yet), added
mipsel15 platform to overcome this

NOTE:  clients and server are compatible from version [r58](https://code.google.com/p/vtuner/source/detail?r=58) on

### [R61](https://code.google.com/p/vtuner/source/detail?r=61) release note: ###
I've added support for up to three different frontend modes for the client. Mode can be switched while e2 is running (tuner configuration, choose vtuner and switch tuner type)

The modes are given as parameter to vtunerc.mipsel, possible values are:
  * -s2: register DVB-S2 frontend, but connect to any DVB-S or -S2 server
  * -S2: register DVB-S2 frontend, connect to DVB-S2 server
  * -s: register DVB-S frontend, but connect to any DVB-S or -S2 server
  * -S: register DVB-S frontend, connect to DVB-S server
  * -c: register DVB-C frontend, connect to DVB-C server
  * -t: register DVB-T frontend, connect to DVB-T server

You should edit /etc/vtunerc.conf after installation on your box:
```
DAEMON="/usr/sbin/vtunerc.mipsel"
OPTIONS="-s2 -c -t"
```
**NOTE**: The old vtunercs, vtunercc or vtunerct calling convention is still supported, but this limits the client to one frontend.

**NOTE**: the mipsel server can't distinguish between DVB-S2 and DVB-S, you should not use -S2 if you want to connect to a mipsel box.

**NOTE**: dvb-modules package must be 20100605-[r0](https://code.google.com/p/vtuner/source/detail?r=0) or later