
Unlike HTTP(S) which is designed to retrieve web pages, File Transfer Protocol (FTP) is designed to transfer files. It is very efficient for file transfer, and when all conditions are equal, it can achieve higher speed than HTTP.

Example commands defined by the FTP protocol are:
- `USER` is used to input the username
- `PASS` is used to input the password
- `RETR` (retrieve) is used to download a file from the FTP server to the client
- `STOR` (store) is used to upload a file from the client to the FTP server

FTP listens on TCP port 21 by default , data transfer is conducted via another connection from the client to the server. explined below

 **Aktivt läge (PORT)**
- Klienten säger: “Jag lyssnar på port X, anslut till mig.”
- Servern öppnar en anslutning _till klienten_ från sin port 20.
- Problem: fungerar dåligt bakom NAT/firewall eftersom servern försöker initiera till klienten.
 **Passivt läge (PASV)**
- Klienten säger: “Ge mig en port jag kan ansluta till.”
- Servern öppnar en lyssnande port (ofta slumpad) och berättar för klienten.
- Klienten gör sedan anslutningen.
- Detta fungerar bättre bakom NAT/firewalls → därför används nästan alltid idag.

------
some usefull commands when first connecting
username might be anonymous
we can just hit enter on passwords
`ls` to list 
`type ascii` switch to ascii mode as this is a text file
`get coffe.txt` to retrieve the file from server on client machine
