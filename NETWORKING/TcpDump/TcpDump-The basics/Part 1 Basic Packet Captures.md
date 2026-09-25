### Specify The Network Interface

`tcpdump -D` ----> running this commands show all interfaces
`tcpdump -i <interface>` ----> you can write the interface name in order to listen to the one that you wanna listen to
`tcpdump -i any` -------> listen from all interfaces
### write out to a file 
`-w` flag
`tcpdump -i eth0 -w <FileName>` -------> you specify and you will get out the capture in a file with .pcap extension and you wont see the packets live meaning scrolling with the -w flag

### Read captures from a file
`-r` flag
`tcpdump -i eth0 -r <FileName` --------> if you already have a save .pcap file you can read it with the help of this command

### Limit the Number of Captured Packet
`-c` flag
`tcpdump -i eth0 -c <numberOfToCapture>` ----> if you put for example 10 you will get 10 packet captures and then it will stop capturing


### Do not Resolve IP addresses and port numbers
`-n` and `-nn` flag
meaning tcpdump will print out friendly domain names where possible. To avoid make such DNS lookups provide the flag `-n` and `-nn` for both ip and port
`tcpdump -i eth0 -n` -----> will not resolve ip
`tcpdump -i eth0 -nn` -----> will not resolve both IP and Port; for example without `-nn` flag it would resolve 80 to http but with this `-nn` flag it would show 80


### Produce more verbose OutPut
`-v` and `-vv` and `-vvv` flag
`tcpdump -i eth0 -v` ---> `-v` flag produce slightly more verbose output. according to the man page will print "time to live, identification, total lenth and options in an ip packet"


--------------------
### Summary and Examples

The table below provides a summary of the command line options that we covered.

|Command|Explanation|
|---|---|
|`tcpdump -i INTERFACE`|Captures packets on a specific network interface|
|`tcpdump -w FILE`|Writes captured packets to a file|
|`tcpdump -r FILE`|Reads captured packets from a file|
|`tcpdump -c COUNT`|Captures a specific number of packets|
|`tcpdump -n`|Don’t resolve IP addresses|
|`tcpdump -nn`|Don’t resolve IP addresses and don’t resolve protocol numbers|
|`tcpdump -v`|Verbose display; verbosity can be increased with `-vv` and `-vvv`|

Consider the following examples:

- `tcpdump -i eth0 -c 50 -v` captures and displays 50 packets by listening on the `eth0` interface, which is a wired Ethernet, and displays them verbosely.
- `tcpdump -i wlo1 -w data.pcap` captures packets by listening on the `wlo1` interface (the WiFi interface) and writes the packets to `data.pcap`. It will continue till the user interrupts the capture by pressing CTRL-C.
- `tcpdump -i any -nn` captures packets on all interfaces and displays them on screen without domain name or protocol resolution.