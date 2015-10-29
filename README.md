These are known-good configurations for a TP-Link TL-WR703N flashed to
[OpenWRT](https://openwrt.org/)
[Barrier Breaker](http://downloads.openwrt.org/barrier_breaker/14.07/),
a copy of which is included here for convenience.

WAP - Gateway Router
===

The directory `wap-router` has the following characteristics:

* It creates a wifi network called `703n` with password `703n703n`.

* It connects to the LAN, using DHCP, on its single Ethernet jack. If
  there is no LAN connection, it still provides connectivity among
  wifi-connected clients.

* The wifi network is on 192.168.64.0/24, and it runs its own DHCP
  server for wifi-connected clients.

* Traffic is NATed between the LAN and the wifi network.

* You can ssh root@192.168.64.1 if you're connected via its wifi. You
  can also ssh through the LAN.

I believe this is a "wireless access point in a gateway router
configuration," but I am never really sure I understand networking
terminology. I use this setup for two purposes:

1. I keep a 703N in the car for road trips so that my kids can play
Pocket Minecraft using the WLAN. There's no internet access, but the
AP routes among the devices.

1. If I have an Ethernet-only internet connection while traveling and
wish to use a wireless-only device such as a tablet, this works great.

WAP - Client
===

The directory `sta-client` puts the device in client mode with a DHCP
server on the LAN side.

* Connects to an existing wireless network called `703n` with the
  password `703n703n`.

* Hands out DHCP addresses in the range 192.168.48.x to devices
  connected to the Ethernet jack.

* Using masquerading, lets the 192.168.48.x devices talk to the
  wireless network.

The purpose of this setup is to let an Ethernet-only device talk to a
wireless network. Without an inexpensive solution like this, you would
have to run a long Ethernet cable somewhere or buy a power-line
communication device, which can be expensive and annoying.

General Tips
===

* For ease of administration, consider installing luci. While
  connected to a working LAN: `opkg update && opkg install luci &&
  /etc/init.d/uhttpd enable && /etc/init.d/uhttpd start`

* To install either of these configurations, scp the `etc/config`
  directory's contents over to the router, preferably after putting in
  your own SSID/password in the right places. Then reboot the router.
