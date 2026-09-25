# Use Cases

When investigating a case, a security analyst should know how to extract hostnames, DNS queries, and user agents to hunt low-hanging fruits after viewing the statistics and creating an investigation plan. The most common four use cases for every security analyst are demonstrated below. If you want to learn more about the mentioned protocols and benefits of the extracted info, please refer to the [Wireshark Traffic Analysis](https://tryhackme.com/room/wiresharktrafficanalysis) room.

  
## Extract Hostnames

```bash
user@ubuntu$ tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname     
92-rkd
92-rkd
T3400

T3400

60-alfb-sec2
60-alfb-sec2

aminott
...
```

The above example shows how to extract hostnames from DHCP packets with TShark. However, the output is hard to manage when multiple duplicate values exist. A skilled analyst should know how to use native Linux tools/utilities to manage and organise the command line output, as shown below.  

```shell
user@ubuntu$ tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname | awk NF | sort -r | uniq -c | sort -r
     26 202-ac
     18 92-rkd
     14 93-sts-sec
... 
```

Now the output is organised and ready to process/use. The logic of the query is explained below.

|                                                                |                                                                                     |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Query**                                                      | **Purpose**                                                                         |
| `tshark -r hostnames.pcapng -T fields -e dhcp.option.hostname` | Main query.  <br>Extract the DHCP hostname value.                                   |
| `awk NF`                                                       | Remove empty lines.                                                                 |
| `sort -r`                                                      | Sort recursively before handling the values.                                        |
| `uniq -c`                                                      | Show unique values, but calculate and show the number of occurrences.               |
| `sort -r`                                                      | The final sort process.  <br>Show the output/results from high occurrences to less. |

  
## Extract DNS Queries

Matches filter

```shell
user@ubuntu$ tshark -r dns-queries.pcap -T fields -e dns.qry.name | awk NF | sort -r | uniq -c | sort -r
     96 connectivity-check.ubuntu.com.rhodes.edu
     94 connectivity-check.ubuntu.com
      8 3.57.20.10.in-addr.arpa
      4 e.9.d.b.c.9.d.7.1.b.0.f.a.2.0.2.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
      4 0.f.2.5.6.b.e.f.f.f.b.7.2.4.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa
      2 _ipps._tcp.local,_ipp._tcp.local
      2 84.170.224.35.in-addr.arpa
      2 22.2.10.10.in-addr.arpa
```

  
## Extract User Agents
```shell
user@ubuntu$ tshark -r user-agents.pcap -T fields -e http.user_agent | awk NF | sort -r | uniq -c | sort -r
      6 Mozilla/5.0 (Windows; U; Windows NT 6.4; en-US) AppleWebKit/534.10 (KHTML, like Gecko) Chrome/8.0.552.237 Safari/534.10
      5 Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:100.0) Gecko/20100101 Firefox/100.0
      5 Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.32 Safari/537.36
      4 sqlmap/1.4#stable (http://sqlmap.org)
      3 Wfuzz/2.7
      3 Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)
```