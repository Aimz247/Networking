
Packet Filtering Parameters | Capture & Display Filters  

There are two dimensions of packet filtering in TShark; live (capture) and post-capture (display) filtering. These two dimensions can be filtered with two different approaches; using a predefined syntax or Berkeley Packet Filters (BPF). TShark supports both, so you can use Wireshark filters and BPF to filter traffic. As mentioned earlier, TShark is a command-line version of Wireshark, so we will need to use different filters for capturing and filtering packets. A quick recap from the [Wireshark: Packet Operations](https://tryhackme.com/r/room/wiresharkpacketoperations) room:

|   |   |
|---|---|
|**Capture Filters**|Live filtering options. The purpose is to **save** only a specific part of the traffic. It is set before capturing traffic and is not changeable during live capture.|
|**Display Filters**|Post-capture filtering options. The purpose is to investigate packets by **reducing the number of visible packets**, which is changeable during the investigation.|

Capture filters are used to have a specific type of traffic in the capture file rather than having everything. Capture filters have limited filtering features, and the purpose is to implement a scope by range, protocol, and direction filtering. This might sound like bulk/raw filtering, but it still provides organised capture files with reasonable file size. The display filters investigate the capture files in-depth without modifying the packet.

|   |   |
|---|---|
|**Parameter**|**Purpose**|
|-f|Capture filters. Same as BPF syntax and Wireshark's capture filters.|
|-Y|Display filters. Same as **Wireshark's display filters.**|

Check out the [**Wireshark: Packet Operations**](https://tryhackme.com/room/wiresharkpacketoperations) room (Task 4 & 5) if you want to review the principles of packet filtering.