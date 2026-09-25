
### OS detection
You can enable OS detection by adding the `-O` flag
`nmap <ip> -O` ---> this will show you or guess the target OS


### Services and Version Detection
`nmap <ip> -sV` --> you can show what services version are running on the port you scan

### Version Detection, OS detection, Trace route
`nmap <ip> -A`  ----> this `-A` meaning all will show you the services, OS detection an traceroute among other things

### Forcing the Scan
`nmap <ip> -Pn`
When we run our port scan, such as using `-sS`, there is a possibility that the target host does not reply during the host discovery phase (e.g. a host doesn’t reply to ICMP requests). Consequently, Nmap will mark this host as down and won’t launch a port scan against it. We can ask Nmap to treat all hosts as online and port scan every host, including those that didn’t respond during the host discovery phase. This choice can be triggered by adding the `-Pn` option.


------------------
### Summary

| Option | Explanation                                          |
| ------ | ---------------------------------------------------- |
| `-O`   | OS detection                                         |
| `-sV`  | Service and version detection                        |
| `-A`   | OS detection, version detection, and other additions |
| `-Pn`  | Scan hosts that appear to be down                    |