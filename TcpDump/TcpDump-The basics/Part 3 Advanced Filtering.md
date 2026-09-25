
check `pcap-filter` manual page `man pcap-filter`
- `greater LENGTH`: Filters packets that have a length greater than or equal to the specified length
- `less LENGTH`: Filters packets that have a length less than or equal to the specified length
### Binary operations
A binary operation works on bits; i.e.,  zeroes and ones. An operation takes one or two bits and returns one bit. 
`&` (And) takes two bits and returns 0 unless both inputs are 1, as shown in the table below.

| Input 1 | Input 2 | Input1 `&` Input 2 |
| ------- | ------- | ------------------ |
| 0       | 0       | 0                  |
| 0       | 1       | 0                  |
| 1       | 0       | 0                  |
| 1       | 1       | 1                  |

`|` (Or) takes two bits and returns 1 unless both inputs are 0. This is shown in the table below.

| Input 1 | Input 2 | Input 1 `\|` Input 2 |
| ------- | ------- | -------------------- |
| 0       | 0       | 0                    |
| 0       | 1       | 1                    |
| 1       | 0       | 1                    |
| 1       | 1       | 1                    |

`!` (Not) takes one bit and inverts it; an input of 1 gives 0, and an input of 0 gives 1, as shown in the table below.

| Input 1 | `!` Input 1 |
| ------- | ----------- |
| 0       | 1           |
| 1       | 0           |

-------------------

### Filtering by Header Bytes
Tcpdump lets you filter on protocol header bytes using the syntax:  
`proto[expr:size]`  

- **proto** → protocol (e.g. `ether`, `ip`, `tcp`, `udp`, `arp`, `icmp`, `ip6`)  
- **expr** → byte offset (0 = first byte)  
- **size** → number of bytes (optional: 1, 2, or 4; default = 1)  

#### Examples
`ether[0] & 1 != 0` ----> capture packets sent to a multicast Ethernet address  
`ip[0] & 0xf != 5` ----> capture IP packets with options set  

---

### Filtering TCP Flags
Special case: you can filter by TCP flags with `tcp[tcpflags]`.  

- `tcpdump "tcp[tcpflags] == tcp-syn"` ----> capture only TCP SYN packets  
- `tcpdump "tcp[tcpflags] & tcp-syn != 0"` ----> capture all packets with SYN flag set  
- `tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"` ----> capture packets with SYN or ACK set  

#### TCP Flags
- `tcp-syn` ----> Synchronize  
- `tcp-ack` ----> Acknowledge  
- `tcp-fin` ----> Finish  
- `tcp-rst` ----> Reset  
- `tcp-push` ----> Push  


--------------------
### Example: Capturing a TCP 3-Way Handshake
A TCP handshake is made of 3 packets: SYN → SYN/ACK → ACK.  
We can filter each step using `tcp[tcpflags]`.

1. **SYN (client → server)**  
   `tcpdump "tcp[tcpflags] == tcp-syn"` ----> capture packets starting the handshake  

2. **SYN/ACK (server → client)**  
   `tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"` ----> capture packets with both SYN and ACK set  

3. **ACK (client → server)**  
   `tcpdump "tcp[tcpflags] == tcp-ack"` ----> capture packets completing the handshake  

 Together, these three filters let you observe the full TCP connection setup.  
