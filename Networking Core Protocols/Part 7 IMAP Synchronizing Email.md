IMAP  (Internet Message Access Protocol)
IMAP allows synchronizing read, moved, and deleted messages, IMAP is quite convenient when you check your email via multiple clients. Unlike POP3, which tends to minimize server storage as email is downloaded and deleted from the remote server, IMAP tends to use more storage as email is kept on the server and synchronized across the email clients.

IMAP server listens on TCP port 143 by default we use telnet to connect `telnet <ip> 143`

The IMAP protocol commands are more complicated than the POP3 protocol below are some examples:
- `LOGIN <username> <password>` authenticates the user
- `SELECT <mailbox>` selects the mailbox folder to work with
- `FETCH <mail_number> <data_item_name>` Example `fetch 3 body[]` to fetch message number 3, header and body.
- `MOVE <sequence_set> <mailbox>` moves the specified messages to another mailbox
- `COPY <sequence_set> <data_item_name>` copies the specified messages to another mailbox
- `LOGOUT` logs out
```bash
#example commands flow that you type 
A LOGIN strategos <lösenord>
B SELECT inbox
C FETCH 3 body[]
D LOGOUT
```



