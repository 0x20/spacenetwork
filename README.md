# spacenetwork
Documentation and configuration of the network at 0x20.be

![Diagram](https://cdn.rawgit.com/0x20/spacenetwork/master/spacenetwork.svg)

To edit the diagrams please use [draw.io](https://www.draw.io/?url=https%3A%2F%2Fraw.githubusercontent.com%2F0x20%2Fspacenetwork%2Fmaster%2Fspacenetwork.svg). After editing export as SVG and select "Include a copy of my diagram".

# More info

Bart, Mirko and Lieven worked on the network tonight.

The old router has been replaced by a APU1D4 running pfSense firewall (http://www.pcengines.ch/apu1d4.htm). This firewall is connected to the new Telenet internet and to the WirelessBelgium internet links. Mirko configured failover: if the Telenet is down, internet is accessible via WirelessBelgium. To Do: BGP for WB.

The first 32 ports of the Cisco 4948 switch in the rack are usable for equipment in the space. Switch and firewall has been labeled: https://imgur.com/a/RTpSj.

Systems on the old LAN (172.22.32.0/24) used static DHCP assignments. These assignments have been transplanted to the new firewall in the new LAN 10.20.0.0/16, keeping the last byte. 

Some systems probably use a fixed IP address, no DHCP, they are still reachable if you configure your PC with a fixed IP in the old LAN: 172.22.32.0/24
 * 172.22.32.3    gatekeeper 00:00:24:c8:99:cc (gatekeeper is still working, opens the gate)
 * 172.22.32.4    kimball    38:60:77:3e:ab:24

We identified these unknown systems that are still using an old IP-address:
 * 172.22.32.20
 * 172.22.32.89
 * 172.22.32.102
These systems should be added to the static dhcp assignments on the firewall with their new IP-addresses (10.20.0.x). Go to https://apurouter.0x20.be > Services > DHCP Server > DHCP Static Mappings > [+] > Fill in MAC Address, IP Address and Hostname.> Save
