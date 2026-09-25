TLS (Transport Layer Security) is added to existing protocols to protect communication confidentiality, integrity and authenticity.
HTTP -----------> HTTPS
POP3 -----------> POP3S
SMTP -----------> SMTPS
IMAP ------------> IMAPS
TELNET unsecure -------------> SSH used instead

In the old days attackers set their network card in promiscuous mode, i.e., to capture all packet, including those not destined to it. They would through all the packets captures and obtain the login credentials of unsuspecting victims. There was nothing a user could do to prevent their login password from being sent in cleartext. Nowdays, it has become uncommon to come across a service that sends login credentials in cleartext.


-----------
Netscape Communication recognised the need of secure communication on the World Wide Web in the early 1990s.
They eventually developed SSL --------> Secure Socket Layer and released SSL 2.0 in 1995 as the first public version.
In 1999, the internet Engineering Task Force (IETF) developed TLS (Transport Layer Security). 
Although very similar, TLS 1.0 was an upgrade to SSL 3.0 and offered various improved security measures. In **2018**, TLS had a significant overhaul of its protocol and TLS 1.3 was released. The purpose is not to remember the exact dates but to realise the amount of work and time put into developing the current version of TLS, i.e., TLS 1.3. Over more than two decades, there have been many things to learn from and improve with every version.

Like SSL, its predecessor, TLS is a cryptographic protocol operating at the OSI model’s transport layer. It allows secure communication between a client and a server over an insecure network. By secure, we refer to confidentiality and integrity; TLS ensures that no one can read or modify the exchanged data.

-----
# Technical Background

The first step for every server (or client) that needs to identify itself is to get a signed TLS certificate. Generally, the server administrator creates a Certificate Signing Request (CSR) and submits it to a Certificate Authority (CA);
The CA verifies the CSR and issues a digital certificate. Once the (Signed) Certificate is received, it can be used to identify the server (or the client) to others, who can confirm the validity of the signature. 
For a host to confirm the validity of a signed certificate, the certificate of the signing authorities need to be installed on the host.
In the non-digital world, this is similar to recognising the stamps of various authorities. 
the image shows the isntalled authorities on the web browser
![[Pasted image 20251005221023.png]]
Generally speaking, getting a certificate signed requires paying an annual fee. However, [Let’s Encrypt](https://letsencrypt.org/) allows you to get your certificate signed for free.

Finally, we should mention that some users opt to create a self-signed certificate. A self-signed certificate cannot prove the server’s authenticity as no third party has confirmed it.