## Packet Filtering

Wireshark has a powerful filter engine that helps analysts to narrow down the traffic and focus on the event of interest. Wireshark has two types of filtering approaches:  
Capture and Display Filters.

- Capture filters are used for "**Capturing"** only the packets valid for the used filter.
- Display filters are used for **"Viewing"** the packets valid for the used filter.

Filters are specific queries designed for protocols available in Wireshark's official protocol reference. Whole the filters are only the option to investigate the event of interest, there are two different ways to filter traffic and remove noise from the capture file. The first one uses queries, and the second uses the right-click. Wireshark provides a powerful GUI, and <span style="color: #1b4cca;"><span style="color: #ffffff;"><span>and there is a golden rule for analysts who don't want to write queries for basic tasks:</span> **"If you can click on it, you can filter and copy it"**<span>.</span></span></span>

* * *

## Apply as Filter

&nbsp;This is the most basic way of filtering traffic. While investigating a capture file, you can click on the filed you want to filter and use the "right-click menu" or **"Analyse ---> Apply as Filter"** menu to filter the specific value. Once you apply the filter, Wireshark will generate the required filter query, apply it, show the packets according to your choice, and hide the unselected packets from the packet list pane. Note that the number of total and displayed are always shown on the status bar.  
![https://tryhackme-images.s3.amazonaws.com/user-uploads/6131132af49360005df01ae3/room-content/463abd0a5cad55831b54a37c17092505.png](463abd0a5cad55831b54a37c17092505.png)

* * *

## Conversation Filter

When you use the "Apply as a Filter" option, you will filter only a single entity of the packet. This option is a good way of investigating a particular value in packets. However, suppose you want to investigate a specific packet number and all linked packets by focusing on IP addresses and port number. In that case, the "Conversation Filter" option helps you view only the related packets and hide the rest of the packets easily. You can use the "right-click menu" or !Analyse ---> Conversation Filter" menu to filter conversations.  
![33adea4a268cb3da788ac76fd54905cf.png](33adea4a268cb3da788ac76fd54905cf.png)

* * *

## Colourise Conversation

This option is similar to the "Conversation Filter" with one difference. It highlights the linked packets without applying a display filter and decreasing the number of viewed packets. This option works with the "Colouring Rules" option add changes the packet colours without considering the previously applied colour rule. You can use the "right-click menu" or **"View ---> Colourise Conversation"** menu to colourise a linked packet in a single click. Note that you can use the **"View ---> Colourise Conversation ---> Reset Colourisation"**   
![a146f738825026b0b218dfe4223a753f.png](a146f738825026b0b218dfe4223a753f.png)

* * *

## Prepare as Filter

Similar to "Apply as Filter", this option helps analysts create display filter using the "right-click" menu. However, unlike the previous one, this model does not apply the filters after the choice. It adds the required query to the pane and waits for the execution command (enter) or another chosen filtering option by using the "**..and/or.."** from the "right-click menu"   
![5d88ed197d1d13cc85f6da20db28f382.png](5d88ed197d1d13cc85f6da20db28f382.png)

* * *

## Apply as Column

By default, the packet list pane provides basic information about each packet. You can use the "right-click menu" or "Analyse ---> Apply as Column" menu to add columns to the packet list pane. Once you click on a value and apply it as a column, it will be visible on the packet list pane. This function helps analysts examine the appearance of a specific value/field across the available packets in the capture file. You can enable/disable the columns shown in the packet list pane by clicking on top of the packet list pane.  
![b961479ded96ba65e6c500ca5a1d5955.png](b961479ded96ba65e6c500ca5a1d5955.png)

* * *

## Follow Stream

Wireshark display everything in packet portion size. However, it is possible to reconstruct the streams and view the raw traffic as it is presented at the application level. Following the protocol, streams help analysts recreate the application-level data and understand the event of interest. It is also possible to view the unecrypted protocol data like usernames, passwords and other transferred data.

You can use the "right-click menu" or **"Analyse ---> Follow TCP/UDP/HTTP Stream"** menu to follow traffic streams. Streams are shown in a separate dialogue box; packets originating from the server are highlighted with blue, and those originating from the clients are highlighted with red.  
![4d3a3c27bb7b226ea1db2db699cbc6f4.png](4d3a3c27bb7b226ea1db2db699cbc6f4.png)

Once you follow a stream, Wireshark automatically creates and applies the required filter to view specific stream. Remember, once a filter is applied, the number of the viewed packets will change. You will need to use the "X button" located on the right upper side of the display filter bar to remove the display filter and view all available packets in the capture file.