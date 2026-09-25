This Capture condition mode only works in sniffing mode, meaning you can not open a already written out file with conditions it will give you an error

|   |   |
|---|---|
|**Parameter**|**Purpose**|
||Define capture conditions for a single run/loop. STOP after completing the condition. Also known as "Autostop".|
|-a|- **Duration:** Sniff the traffic and stop after X seconds. Create a new file and write output to it.  <br>    <br><br>- `tshark -w test.pcap -a duration:1`<br><br>- **Filesize:** Define the maximum capture file size. Stop after reaching X file size (KB).<br><br>- `tshark -w test.pcap -a filesize:10`<br><br>- **Files:** Define the maximum number of output files. Stop after X files.<br><br>- `tshark -w test.pcap -a filesize:10 -a files:3`|
||Ring buffer control options. Define capture conditions for multiple runs/loops. (INFINITE LOOP).|
|-b|- **Duration:** Sniff the traffic for X seconds, create a new file and write output to it.   <br>    <br><br>- `tshark -w test.pcap -b duration:1`<br><br>- **Filesize:** Define the maximum capture file size. Create a new file and write output to it after reaching filesize X (KB).<br><br>- `tshark -w test.pcap -b filesize:10`<br><br>- **Files:** Define the maximum number of output files. Rewrite the first/oldest file after creating X files.<br><br>- `tshark -w test.pcap -b filesize:10 -b files:3`|