HTTPS stands for Hypertext Transfer Protocol Secure. It is basically HTTP over TLS. 
Requesting a page over HTTPS will require the following three steps (after resolving the domain name meaning domain name to dns)
1. Establish a TCP-three-way handshake with the target server
2. Establish a TLS session
3. Communicate using the HTTP protocol; for example, issue HTTP requests, such as GET / HTTP/1.1

The screenshot below shows that a TCP session is established in the first three packets, marked with `1`. Then, several packets are exchanged to negotiate the TLS protocol, marked with `2`. `1` and `2` are where the **TLS negotiation and establishment** take place.
Finally, HTTP application data is exchanged, marked with `3`. Looking at the Wireshark screenshot, we see that it says “Application Data” because there is no way to know if it is indeed HTTP or some other protocol sent over port 443.
![[Pasted image 20251005222129.png]]As expected, if one tries to follow the stream of packets and combine all their contents, they will only get gibberish, as shown in the screenshot below. The exchanged traffic is encrypted; the red is sent by the client, and the blue is sent by the server. There is no way to know the contents without acquiring the encryption key.
![[Pasted image 20251005222333.png]]

-----
# Getting the Encryption key

Adding TLS to HTTP leads to all the packets being encrypted. We can no longer see the contents of the exchange packets unless we get access to the private key. Although it is improbable that we will have access to the keys used for encryption in a TLS session, we repeated the above screenshots after providing the decryption key to wireshark. The TCP and TLS handshakes don not change; the main difference start with the HTTP protocol marked 3, For instance, we can see when the client issues a `GET`
![[Pasted image 20251005222710.png]]

If you want to see the data exchanged, now is your chance! It is still regular HTTP traffic hidden from prying eyes.
![[Pasted image 20251005222738.png]]
The key takeaway is that TLS offered security for HTTP without requiring any changes in the lower or higher layer protocols. In other words, TCP and IP were not modified, while HTTP was sent over TLS the way it would be sent over TCP.