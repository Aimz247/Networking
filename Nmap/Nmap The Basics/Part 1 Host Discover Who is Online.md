
- P range using `-`: If you want to scan all the IP addresses from 192.168.0.1 to 192.168.0.10, you can write `192.168.0.1-10`
- IP subnet using `/`: If you want to scan a subnet, you can express it as `192.168.0.1/24`, and this would be equivalent to `192.168.0.0-255`
- Hostname: You can also specify your target by hostname, for example, `example.thm`
Let’s say you want to discover the online hosts on a network. Nmap offers the `-sn` option, i.e., ping scan. However, don’t expect this to be limited like `ping`. 

### Scanning a "Local" Network
`nmap -sn 192.168.0.66/24`
because we are scanning the local network, where we are connected via Ethernet or WiFi we can lookup the MAC addresses of the devices. Consequently, we can figure out the network card vendors, which is beneficial information as it can help us guess the type of target device(s).

### Scanning a "Remote" Network
On this context, "remote" means that at least one router separates our system from this local network. As a result, all our traffic to the target system mist go through one or more routers. Unlike scanning a local network, we cannot send an ARP request to the target
`nmap -sn 10.0.0.0/24`



It is worth noting that we can have more control over how Nmap discovers live hosts such as `-PS[portlist]`, `-PA[portlist]`, `-PU[portlist]` for TCP SYN, TCP ACK, and UDP discovery via the given ports.

As a final point, Nmap offers a list scan with the option `-sL`. This scan only lists the targets to scan without actually scanning them. For example, `nmap -sL 192.168.0.1/24` will list the 256 targets that will be scanned. This option helps confirm the targets before running the actual scan.