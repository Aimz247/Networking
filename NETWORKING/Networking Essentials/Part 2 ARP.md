In normal when two host communicate over a network (not the local network), an IP packet is encapsulated within a data link frame as it travels over layer 2.
Remember that the two common data link layers are 
- Ethernet (IEEE 802.3)
- WiFi (IEEE 802.11)
Whenever one host need to communicate with another host on the same Ethernet or WiFi, it must send the IP packet withing a data link layer frame. Although it know the IP address of the target host, it needs to look up the target's MAC address so the proper data link header can be created.

MAC address is a 48 but number typically represented in hexadecimal for example `7C:DF:A1:D3:8C:5C` and  `44:DF:65:D8:FE:6C`

The devices on the same Ethernet network do not need to know each other's MAC addresses all the time; they only need to know each other's MAC addresses while communicating.

APR (Address Resolution Protocol) makes it possible to find the MAC address of another device on the Ethernet.

 In the example below, a host with the IP address `192.168.66.89` wants to communicate with another system with the IP address `192.168.66.1`. It sends an ARP Request asking the host with the IP address `192.168.66.1` to respond. The ARP Request is sent from the MAC address of the requester to the broadcast MAC address, `ff:ff:ff:ff:ff:ff` as shown in the first packet. The ARP Reply arrived shortly afterwards, and the host with the IP address `192.168.66.1` responded with its MAC address. From this point, the two hosts can exchange data link layer frames.
```bash
user@TryHackMe$ tshark -r arp.pcapng -Nn
    1 0.000000000 cc:5e:f8:02:21:a7 → ff:ff:ff:ff:ff:ff ARP 42 Who has 192.168.66.1? Tell 192.168.66.89
    2 0.003566632 44:df:65:d8:fe:6c → cc:5e:f8:02:21:a7 ARP 42 192.168.66.1 is at 44:df:65:d8:fe:6c
```

If we use `tcpdump`, the packets will be displayed differently. It uses the terms ARP **Request** and ARP **Reply**. For your information, the output is shown in the terminal below.
```shell
user@TryHackMe$ tcpdump -r arp.pcapng -n -v
17:23:44.506615 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.66.1 tell 192.168.66.89, length 28
17:23:44.510182 ARP, Ethernet (len 6), IPv4 (len 4), Reply 192.168.66.1 is-at 44:df:65:d8:fe:6c, length 28
```

An ARP Request or ARP Reply is not encapsulated within a UDP or even IP packet; it is encapsulated directly within an Ethernet frame. The following ARP Reply shows this.

![Wireshark showing an ARP Reply encapsulated directly within an Ethernet frame.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1719849185596.png)  

ARP is considered layer 2 because it deals with MAC addresses. Others would argue that it is part of layer 3 because it supports IP operations. What is essential to know is that ARP allows the translation from layer 3 addressing to layer 2 addressing.