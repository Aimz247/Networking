
- SSID: The network "name" that you see when you try and connect
- ESSID: An SSID that *may* apply to multiple access points, eg a company office, normally forming a bigger network. For aircrack they normally refer to the network you are attacking.
- BSSID: An access point MAC (hardware) address.
- WPA2-PSK: Wifi network that you connect to by providing a pre-shared password that's the same for everyone.
- WPA2-EAP: Wifi networks that you authenticate to by providing a username and password, which is sent to a RADIUS server.
- RADIUS: A server for authenticating clients, not just for wifi.
------------

<span style="font-size: 30px;">WPA(2)</span> --> authentication is the 4 way handshake.
Most home networks, and many others, use WPA(2) personal. If you have to login with a password and it is not WEP, then it is WPA(2) personal. 
WPA2-EAP uses RADIUS servers to authenticate, so if you have to enter a username and password in order to connect then it is that.

<span style="font-size: 25px;">WEP</span> is unsecure WEP stands for Wired Equvalent Privacy which can be broken by capturing enough packets to guess the key via statistical methods.
