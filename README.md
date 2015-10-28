This is a known-good configuration for a TP-Link TL-WR703N flashed to
OpenWRT "Barrier Breaker," with the following characteristics:

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

For ease of administration, consider installing luci. While connected
to a working LAN: `opkg update && opkg install luci &&
/etc/init.d/uhttpd enable && /etc/init.d/uhttpd start`

Extra bonus
===

The sta_client branch is a known-bad (WIP) configuration for the same
 router in client mode. The purpose is to give a network connection
 via wifi to a wired device plugged into the 703n's Ethernet port.
