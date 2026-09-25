Running your scan at its normal speed might trigger an IDS (intrusion detection system) or other security solutions.

`-T1` or `-T 1` or `-T sneaky`
nmap gives sex timing templates 
- paranoid (0)
- sneaky (1)
- polite (2)
- normal (3)
- aggressive (4)
- insane (5)
------------

- `-T0` / `-T paranoid`   ----> **very slow**, maximum stealth, long delays (use when avoiding IDS/IPS)  
- `-T1` / `-T sneaky`     ----> **slow**, highly cautious, used for stealthy probing  
- `-T2` / `-T polite`     ----> **moderate-slow**, reduces network load (good on congested networks)  
- `-T3` / `-T normal`     ----> **default**, balanced speed and reliability  
- `-T4` / `-T aggressive`  ----> **fast**, reduces timing buffers, good on reliable, local networks  
- `-T5` / `-T insane`     ----> **very fast**, minimal delays, for very fast LAN scans (may trigger defenses)

#### Examples
- `nmap -T0 -sS 192.168.1.0/24` ----> stealthy SYN scan, very slow  
- `nmap -T2 -sV example.com`      ----> polite speed, service version detection  
- `nmap -T4 -A 10.0.0.5`         ----> aggressive full scan with OS/service detection

#### Notes / Guidance
- **Higher T ⇒ faster but more likely to be detected.**  
- Use `-T0/-T1` for stealth against IDS or over slow links.  
- Use `-T4/-T5` for quick scans on trusted, local networks.  
- `-T3` (normal) is safe as a default for general-purpose scanning.

### Table example
`nmap -sS 10.10.249.70 -F` ----> for example the command timing with the scan options (`-F` fast scan)

| Timing          | Total Duration |
| --------------- | -------------- |
| T0 (paranoid)   | 9.8 hours      |
| T1 (sneaky)     | 27.53 minutes  |
| T2 (polite)     | 40.56 seconds  |
| T3 (normal)     | 0.15 seconds   |
| T4 (aggressive) | 0.13 seconds   |
we can say that `-T 0` will wait 5 minutes before sending the next package if we check the packets in wireshark
Nmap waited 15 seconds between every two ports when we set the timing to `T1`.
 the waiting dropped to 0.4 seconds for `T2` 

--------------------------
### ### Controlling Parallelism and Rate in Nmap

#### Parallelism (number of simultaneous probes)
`--min-parallelism <num>` and `--max-parallelism <num>`  
Controls how many TCP/UDP probes Nmap may have active **simultaneously** for a host group.

- `--min-parallelism 10` ----> ensure at least 10 parallel probes are used (when possible)  
- `--max-parallelism 200` ---> never exceed 200 parallel probes  

Notes:
- By default Nmap auto-tunes parallelism based on network conditions.  
- On lossy networks Nmap may reduce parallelism (even down to 1).  
- On good networks parallelism can grow to hundreds.  
- Use these options when you want stricter control over load on the network or target.

#### Rate (packets per second)
`--min-rate <pps>` and `--max-rate <pps>`  
Sets the minimum / maximum **packets per second (pps)** Nmap will send for the whole scan.

- `--min-rate 50`  ----> send at least 50 packets/sec overall (if possible)  
- `--max-rate 1000` ---> cap sending to at most 1000 packets/sec overall

Notes:
- The rate applies to the **entire scan**, not per target host.  
- Useful to throttle scans on fragile links or to saturate a fast LAN deliberately.  
- Combining rate and parallelism gives fine-grained control (e.g. low rate + high parallelism vs high rate + low parallelism behave differently).


# Summary

|Option|Explanation|
|---|---|
|`-T<0-5>`|Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)|
|`--min-parallelism <numprobes>` and `--max-parallelism <numprobes>`|Minimum and maximum number of parallel probes|
|`--min-rate <number>` and `--max-rate <number>`|Minimum and maximum rate (packets/second)|
|`--host-timeout`|Maximum amount of time to wait for a target host|