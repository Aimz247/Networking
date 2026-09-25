
### Filtering by Host
`host` and `src host` and `dst host` flag
`tcpdump host example.com -w http.pcap` ----> capture all traffic to and from example.com  
`tcpdump src host <IP>` ----> capture traffic only from the given source IP  
`tcpdump dst host <IP>` ----> capture traffic only to the given destination IP  

### Filtering by Port
`port` and `src port` and `dst port` flag
`tcpdump -i eth0 port 53 -n`  ---> capture all traffic to and from port 53
`tcpdump src port <portnumber>` ----> capture traffic only from the given source port  
`tcpdump dst port <portnumber>` ----> capture traffic only to the given destination port 

### Filtering by Protocol
`tcpdump -i eth0 icmp -n` ----> capture ICMP traffic (e.g. `ping` or `tracert`)  
`tcpdump -i eth0 arp -n` ----> capture ARP traffic (e.g. address resolution requests)  
`tcpdump -i eth0 tcp -n` ----> capture all TCP traffic  
`tcpdump -i eth0 udp -n` ----> capture all UDP traffic  
`tcpdump -i eth0 ip -n` ----> capture all IP packets (default for most captures)  
`tcpdump -i eth0 ip6 -n` ----> capture all IPv6 packets  

### Logical Operators
- `and`: Captures packets where both conditions are true. For example, `tcpdump host 1.1.1.1 and tcp` captures `tcp` traffic with `host 1.1.1.1`.
- `or`: Captures packets when either one of the conditions is true. For instance, `tcpdump udp or icmp` captures UDP or ICMP traffic.
- `not`: Captures packets when the condition is not true. For example, `tcpdump not tcp` captures all packets except TCP segments; we expect to find UDP, ICMP, and ARP packets among the results.

------------------------------

### Summary and Examples

The table below offers a summary of the command line options that we covered.

|Command|Explanation|
|---|---|
|`tcpdump host IP` or `tcpdump host HOSTNAME`|Filters packets by IP address or hostname|
|`tcpdump src host IP` or|Filters packets by a specific source host|
|`tcpdump dst host IP`|Filters packets by a specific destination host|
|`tcpdump port PORT_NUMBER`|Filters packets by port number|
|`tcpdump src port PORT_NUMBER`|Filters packets by the specified source port number|
|`tcpdump dst port PORT_NUMBER`|Filters packets by the specified destination port number|
|`tcpdump PROTOCOL`|Filters packets by protocol; examples include `ip`, `ip6`, and `icmp`|

Consider the following examples:

- `tcpdump -i any tcp port 22` listens on all interfaces and captures `tcp` packets to or from `port 22`, i.e., SSH traffic.
- `tcpdump -i wlo1 udp port 123` listens on the WiFi network card and filters `udp` traffic to `port 123`, the Network Time Protocol (NTP).
- `tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap` will listen on `eth0`, the wired Ethernet interface and filter traffic exchanged with `example.com` that uses `tcp` and `port 443`. In other words, this command is filtering HTTPS traffic related to `example.com`.

For the questions from this task, we will read captured packets from the `traffic.pcap` file. As mentioned earlier, we use `-r FILE` to read from a packet capture file. To test this, try `tcpdump -r traffic.pcap -c 5 -n`; it should display the first five packets in the file without looking up the IP addresses.

Remember that you can count the lines by piping the output via the `wc` command. In the terminal below, we can see that we have 910 packets with the source IP address set to `192.168.124.1`. Please note that we add `-n` to avoid unnecessary delays in attempting to resolve IP addresses. In the example below, we didn’t use `sudo` as reading from a packet capture file does not require `root` privileges.


```shell-session
user@TryHackMe$ tcpdump -r traffic.pcap src host 192.168.124.1 -n | wc
reading from file traffic.pcap, link-type EN10MB (Ethernet)
    910   17415  140616
```