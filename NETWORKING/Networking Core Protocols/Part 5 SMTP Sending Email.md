Simple Mail Transfer Protocol  (SMTP) defines how a mail client talks with a mail server and how a mail server talks with another.

Some commands used by your mail client when it transfers an email to an SMTP server:
- `HELO` or `EHLO` initiates an SMTP session
- `MAIL FROM` specifies the senders email address
- `RCPT TO` specifies the recipient's email address
- `DATA` indicates that the client will begin sending the content of the email message
- `.` is sent on a line by itself to indicate the end of the email message

SMTP server listens on TCP port 25 by default

example flow 
```bash
telenet ip 25
HELO client.thm
MAIL FROM:<aimz@client.thm>
RCPT TO:<strategos@server.thm>
DATA
Subject: Telnet email
Hello, this is a test message sent manually via telnet!

.
QUIT

```