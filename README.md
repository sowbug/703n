This is a known-good configuration for a TP-Link TL-WR703N flashed
to OpenWRT "Barrier Breaker," with the following characteristics:

  - It connects to the LAN on its single Ethernet jack.
  - On the LAN it gets its connection information through DHCP.
  - It creates a wifi network called 703n with password 703n703n.
  - The wifi network is isolated on 192.168.64.0/24.
  - The wifi network runs its own DHCP server for connecting clients.
  - Traffic is NATed between the LAN and the wifi network.

I believe this is a wireless access point in a gateway router
configuration, but I am never really sure I understand networking terminology. I use this setup for two purposes:

  1. I keep a 703N in the car for road trips, and my kids can play
     Pocket Minecraft using the WLAN. There's no internet access, but
     the AP routes among the devices.
  2. If I have an Ethernet jack while traveling and wish to connect with
     a wireless-only device such as a tablet, this works great.