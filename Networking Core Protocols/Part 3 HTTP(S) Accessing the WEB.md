HTTP stands for Hyper Text Transfer Protocol ----> commonly TCP port 80 Less commonly 8080
HTTPS stands for Hyper Text Transfer Protocol Secure -----> commonly TCP port 443 Less commonly 8443
This protocol relies on TCP and defines how your web browser communicates with the web servers

Some of the commands or methods that the web browser commonly issues to the web server are:
 - `GET`: retrieves data from a server, such as an HTML filer or an image.
 - `POST`: allows us to submit new data to the server, such as submitting a form or uploading a file.
 - `PUT`: is used to create a new resource on the server and to update and overwrite existing information.
 - `DELETE`: is used to delete a specific file or resource on the server.
 -----------
 when we used the `telnet` client to connect to the web server running on `10.10.78.35` at port `80`. We had to send a couple of lines: `GET / HTTP/1.1` and `Host: anything` to get the page we wanted. (On some servers, you might get the file without sending `Host: anything`.) You can use this method to access any page and not just the default page `/`. To get `file.html`, you would send `GET /file.html HTTP/1.1`, for instance (`GET /file.html` might work depending on the web server in use). This approach is efficient for troubleshooting as you would be “talking HTTP” with the server.