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

#### IP Addresses
Your operating system's network configuration uses the Domain Name Service (DNS) — a set of servers maintained by Internet Service Providers (ISPs) and other network users — to look up hostnames and get back IP addresses.

IP addresses come in two different varieties: the older IPv4 and the newer IPv6. When you see an address like 127.0.0.1 or 216.58.194.164, those are IPv4 addresses. IPv6 addresses are much longer, such as 2607:f8b0:4005:804::2004, although they can also be abbreviated.

### Localhost
The IPv4 address 127.0.0.1 and the IPv6 address ::1 are special addresses that mean "this computer itself" — for when a client (like your browser) is accessing a server on your own computer.
