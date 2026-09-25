# Command-Line packet analysis Hints
TShark is a text-based tool, and it is suitable for data carving, in-depth packet analysis, and automation with scripts. This strength and flexibility come out of the nature of the CLI tools, as the produced/processed data can be pipelined to additional tools. The most common tools used in packet analysis are listed below.

|   |   |
|---|---|
|**Tool/Utility**|**Purpose and Benefit**|
|**capinfos**|A program that provides details of a specified capture file. It is suggested to view the summary of the capture file before starting an investigation.|
|**grep**|Helps search plain-text data.|
|**cut**|Helps cut parts of lines from a specified data source.|
|**uniq**|Filters repeated lines/values.|
|**nl**|Views the number of shown lines.|
|**sed**|A stream editor.|
|**awk**|Scripting language that helps pattern search and processing.|

Note: Sample usage of these tools is covered in the [Zeek](https://tryhackme.com/room/zeekbro) room.

#### capinfo the .pcap file to analyize before starting an investigation
example:
```shell
user@ubuntu$ capinfos demo.pcapng 
File name:           demo.pcapng
File type:           Wireshark/tcpdump/... - pcap
File encapsulation:  Ethernet
File timestamp precision:  microseconds (6)
Packet size limit:   file hdr: 65535 bytes
Number of packets:   4...
File size:           25 kB
Data size:           25 kB
Capture duration:    30.393704 seconds
First packet time:   2004-05-13 10:17:07.311224
Last packet time:    2004-05-13 10:17:37.704928
Data byte rate:      825 bytes/s
Data bit rate:       6604 bits/s
Average packet size: 583.51 bytes
Average packet rate: 1 packets/s
SHA256:              25a72bdf10339...
RIPEMD160:           6ef5f0c165a1d...
SHA1:                3aac91181c3b7...
Strict time order:   True
Number of interfaces in file: 1
Interface #0 info:
                     Encapsulation = Ethernet (1 - ether)
                     Capture length = 65535
                     Time precision = microseconds (6)
                     Time ticks per second = 1000000
                     Number of stat entries = 0
                     Number of packets = 4...
..
```