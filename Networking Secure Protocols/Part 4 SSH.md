Telnet is risky when all traffic is sent in clear text. anyone sniffing for packets can see the password.
To solution is to use SSH ---> Secure Shell

Side note ---> openSSH is the open-source implementation of SSH. Nowdays, when you use an SSH client, it is most likely based on OpenSSH libraries and source code.

OpenSSH offers several benefits, The list below are few of them 
- `Secure authentication`: Besides password-based authentication, SSH supports public key and two factor authentication.
- `Confidentaility`: OpenSSH provides end-to-end encryption, protecting against eavedropping, Firthermore, it notifies you of new server keys to protext against man-in-the-middle attacks.
- `Integrity`: In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
- `Tunneling`: SSH can create a secure "tunnel" to route other protocols through SSH. This setup leads to a VPN like connection.
- `X11 Forwarding`: If you connect to Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.

you would issue the commands `ssh username@hostname` to connect to an SSH server
if the username is the same as your logged-in username, you only need `ssh hostname`
SSH server listens on port 22
while
Telnet server listens on port 23
