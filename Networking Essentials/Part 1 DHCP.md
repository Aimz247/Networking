Whenever you want to access a network, at the very least, we need to configure the following
- IP address along with subnet mask
- Router (or gateway)
- DNS server
Manually configuring these setting is good option especially for servers.
----
Having an automated way to configure connected devices has many advantages. 
- First, it would save us from manually configuring the network; this is extremely important, especially for mobile devices.
- Secondly, it saves is from address conflicts, i.e., when two devices are configured with the same IP address. 
The solution lies in using `Dynamic Host Configuration Protocol` DHCP.
DHCP is an application-level protocol that relies on UDP; the server listens on UDP port 67, and the client send from UDP port 68. Smartphone and laptops are configured automatically.
![[Pasted image 20251005133804.png]]

DHCP follows four steps:
- DHCP Discover: The client broadcasts a `DHCPDISCOVER` message seeking the local DHCP server if one exists.
- DHCP Offer: The server responds with `DHCPOFFER` message with an IP address available for the client to accept.
- DHCP Request: The client responds with a `DHCPREQUEST` message to indicate that it has accepted the offered IP.
- DHCP Acknowledge: The server responds with a `DHCPACK` message to confitm that the offered IP address is now assigned to this client.
```shell-session
user@TryHackMe$ tshark -r DHCP-G5000.pcap -n
    1   0.000000      0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Discover - Transaction ID 0xfb92d53f
    2   0.013904 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP Offer    - Transaction ID 0xfb92d53f
    3   4.115318      0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Request  - Transaction ID 0xfb92d53f
    4   4.228117 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP ACK      - Transaction ID 0xfb92d53f
```
We notice
- The client starts without any IP network configuration. It only has a MAC address. In the first and third packets, DHCP Discover and DHCP Requrst, the clinet searching for a DHCP server still has no IP network configuration and has not yet used the DHCP server's offered IP address. Therefore it sends packet from the IP address 0.0.0.0 to the broadvast IP address 255.255.255.255
- As for the link layer, in the first and third packets, the client send to the broadcast MAC address, `ff:ff:ff:ff:ff:ff` (not shown in the output above). The DHCP server offers an available IP address along with the network configuration in the DHCP offer. It uses the client's destination MAC address.

At the end of the DHCP process, our device would have received all the configuration needed to access the network or even the Internet. In particular, we expect that the DHCP server has provided us with the following:
- The leased IP address to access network resources
- The gateway to route our packets outside the local network
- A DNS server to resolve domain names (more on this later)

![[Pasted image 20251005134133.png]]

------------

