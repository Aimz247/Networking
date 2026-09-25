
|                  |                                                                                          |
| ---------------- | ---------------------------------------------------------------------------------------- |
| **Parameter**    | **Purpose**                                                                              |
| -h               | - Display the help page with the most common features.<br>- `tshark -h`                  |
| -v               | - Show version info.<br>- `tshark -v`                                                    |
| -D               | - List available sniffing interfaces.<br>- `tshark -D`                                   |
| -i               | - Choose an interface to capture live traffic.<br>- `tshark -i 1`<br>- `tshark -i ens55` |
| **No Parameter** | - Sniff the traffic like tcpdump.<br>- `tshark`                                          |
# Sniffing
When no parameter is chosen and you run tshark it will start sniffing all the traffic.
`tshark -D` will list all available interface
when running without giving a interface name it will use the first available interface to sniff packets
- step 1: `tshark -D` 
- step 2: `tshark -i etho` for example in this we use interface eth0 that was available from the list of the step 1 command

-------------------------

# More params
|               |                                                                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameter** | **Purpose**                                                                                                                                                       |
| -r            | - Read/input function. Read a capture file.<br>- `tshark -r demo.pcapng`                                                                                          |
| -c            | - Packet count. Stop after capturing a specified number of packets.<br>- E.g. stop after capturing/filtering/reading 10 packets.<br>- `tshark -c 10`              |
| -w            | - Write/output function. Write the sniffed traffic to a file.<br>- `tshark -w sample-capture.pcap`                                                                |
| -V            | - Verbose.<br>- Provide detailed information **for each packet**. This option will provide details similar to Wireshark's "Packet Details Pane".<br>- `tshark -V` |
| -q            | - Silent mode.<br>- Suspress the packet outputs on the terminal.<br>- `tshark -q`                                                                                 |
| -x            | - Display packet bytes.<br>- Show packet details in hex and ASCII dump for each packet.<br>- `tshark -x`                                                          |

# example usage of more params

```shell
# here we do with the -r param
tshark -r demo.pcapng
```

```shell
# we see we can combine and i is the interface and -c 2 will only show two packets 
tshark -i etho -c 2
```

```shell
# write data
# here we use interface eth0, we capture only 10 packets and the output will be save in a file with -w parameter called demo.pcap 
tshark -i eth0 -c 10 -w demo.pcap
```

```bash
# reading data
# lets say we have a file that we want to read from we use this commnd
tshark -r demo.pcap
```



```bash
# we can increase the verbosity of each capture the thing without it it only shows one line but with -V flag we see more output
# Note capital V not minor since it will show the version of tshark
# Default view
user@ubuntu$ tshark -r demo.pcapng -c 1
    1   0.000000 145.254.160.237 ? 65.208.228.223 TCP 3372 ? 80 [SYN] Seq=0 Win=8760 Len=0 MSS=1460 SACK_PERM=1 

# Verbosity
user@ubuntu$ tshark -r demo.pcapng -c 1 -V
Frame 1: 62 bytes on wire (496 bits), 62 bytes captured (496 bits)
...
Ethernet II, Src: 00:00:01:00:00:00, Dst: fe:ff:20:00:01:00
...
Internet Protocol Version 4, Src: 145.254.160.237, Dst: 65.208.228.223
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Total Length: 48
    Identification: 0x0f41 (3905)
    Flags: 0x4000, Don't fragment
    Fragment offset: 0
    Time to live: 128
    Protocol: TCP (6)
    Source: 145.254.160.237
    Destination: 65.208.228.223
Transmission Control Protocol, Src Port: 3372, Dst Port: 80, Seq: 0, Len: 0
 ...
```