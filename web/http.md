# HTTP

### URI
`scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]`

Here is an example of a URI: https://en.wikipedia.org/wiki/Fish

This URI has three visible parts, separated by a little bit of punctuation:

`https` is the scheme;
`en.wikipedia.org` is the hostname;
`/wiki/Fish` is the path.

https://en.wikipedia.org/wiki/Oxygen#Discovery

`Oxygen#Discovery` is a fragment. It sends the client to an html id.

https://www.google.com/search?q=fish

`?q=fish` is a query

### Hostnames

Why is it called a hostname? In network terminology, a host is a computer on the network; one that could host services

` http://216.58.194.174/` has an IP address as the hostname (points to Google)

In the terminal, you can use the `host` or `nslookup` program to look up hostnames in DNS

```
$ host www.google.com
www.google.com has address 172.217.31.132

$nslookup www.google.com
Server:		2001:a450:4120:7600:2eff:65ff:fea0:f2f1
Address:	2001:a450:4120:7600:2eff:65ff:fea0:f2f1#53

Non-authoritative answer:
Name:	www.google.com
Address: 172.217.26.36
```

### IP Addresses
Your operating system's network configuration uses the Domain Name Service (DNS) — a set of servers maintained by Internet Service Providers (ISPs) and other network users — to look up hostnames and get back IP addresses.

IP addresses come in two different varieties: the older IPv4 and the newer IPv6. When you see an address like 127.0.0.1 or 216.58.194.164, those are IPv4 addresses. IPv6 addresses are much longer, such as 2607:f8b0:4005:804::2004, although they can also be abbreviated.

### Localhost
The IPv4 address 127.0.0.1 and the IPv6 address ::1 are special addresses that mean "this computer itself" — for when a client (like your browser) is accessing a server on your own computer.

### Ports
HTTP URIs imply a port number of 80
HTTPS URIs imply a port number of 443
We say that a server "listens on" a port, such as 80 or 8000. "Listening" means that when the server starts up, it tells its operating system that it wants to receive connections from clients on a particular port number. When a client (such as a web browser) "connects to" that port and sends a request, the operating system knows to forward that request to the server that's listening on that port.

### Packets
Each packet has the IP addresses of the computer that sent it, and the computer that receives it. 
And (with the exception of some low-level packets, such as ping) it also has the port number for the sender and recipient.
IP addresses distinguish computers; port numbers distinguish programs on those computers.

## HTTP Requests and Responses
An exchange between a server and a client

### Request
HTTP verbs
GET

### Response
The HTTP response is made up of three parts: the status line, some headers, and a response body.

**Status line:** The status line tells the client whether the server understood the request, whether the server has the resource the client asked for, and how to proceed next. It also tells the client which dialect of HTTP the server is speaking.

**Status codes** from status line i.e. `HTTP/1.0 200 OK`.
The numbers 200 and 301 here are HTTP status codes. There are dozens of different status codes. The first digit of the status code indicates the general success of the request. As a shorthand, web developers describe all of the codes starting with 2 as "2xx" codes, for instance — the x's mean "any digit".

- 1xx — Informational. The request is in progress or there's another step to take.
- 2xx — Success! The request succeeded. The server is sending the data the client asked for.
- 3xx — Redirection. The server is telling the client a different URI it should redirect to. The headers will usually contain a Location header with the updated URI. Different codes tell the client whether a redirect is permanent or temporary.
- 4xx — Client error. The server didn't understand the client's request, or can't or won't fill it. Different codes tell the client whether it was a bad URI, a permissions problem, or another sort of error.
- 5xx — Server error. Something went wrong on the server side.

https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

**Headers**
Each header is a line that starts with a keyword, such as Location or Content-type, followed by a colon and a value.
Headers are a sort of metadata for the response.

- Content-type: indicates the kind of data that the server is sending. It includes a general category of content as well as the specific format.
- Content-Length: tells the client how long (in bytes) the response body will be.

**Cookies**
a web feature that lets servers store data on the browser, for instance to keep a user logged in. To set a cookie, the server sends the Set-Cookie header. The browser will then send the cookie data back in a Cookie header on subsequent requests.

**Body**
The headers end with a blank line. Everything after that blank line is part of the response body. If the request was successful (a 200 OK status, for instance), this is a copy of whatever resource the client asked for — such as a web page, image, or other piece of data.

But in the case of an error, the response body is where the error message goes! If you request a page that doesn't exist, and you get a 404 Not Found error, the actual error message shows up in the response body.

### Playing with servers
- `ncat -l 9999`: create a server in your terminal 
- `ncat [hostname][port]`: connect as a client in another terminal 
- `python3 -m http.server 8000`: create a server using python3 
