### Connect Scan
`nmap <ip> -sT` --> this is the connect scan that will try to complete the TCP three-way hadnshake. nmap will establosh a connection and then send `rst, ack` since it does not need to hold the connection alive and communicates. in simpler words it connects if it is alives and terminates directly. it is just to check if it can connect.


### SYN scan (stealth)
`nmap <ip> -sS` --> This is called the syn scan. unlike the connect scan above completing the TCP three-way handshake this scan only sends only a TCP SYN packet. remember the tcp three way handshake syn --> syn,ack --> ack


### Scanning UDP Ports
Although most services use TCP for communication, many use UDP. 
For example ---> DNS, DHCP, NTP (network time protocol), SNMP (simple network management protocol), VoIP (voice over ip)
Remember UDP does not require establishing a connection and tearing it down afterwards.

`nmap <ip> -sU` ---> scans for UDP services. 


### Limiting the Target Ports
nmap scans the most common 1000 ports by default, nmap offers options that we can use to scan what ever port we want

- `-F` is for Fast mode, which scans the 100 most common ports (instead of the default 1000).
- `-p[range]` allows you to specify a range of ports to scan. For example, `-p10-1024` scans from port 10 to port 1024, while `-p-25` will scan all the ports between 1 and 25. Note that `-p-` scans all the ports and is equivalent to `-p1-65535` and is the best option if you want to be as thorough as possible.

-------------------------
### Summary

|Option|Explanation|
|---|---|
|`-sT`|TCP connect scan – complete three-way handshake|
|`-sS`|TCP SYN – only first step of the three-way handshake|
|`-sU`|UDP scan|
|`-F`|Fast mode – scans the 100 most common ports|
|`-p[range]`|Specifies a range of port numbers – `-p-` scans all the ports|