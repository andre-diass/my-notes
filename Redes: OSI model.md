# Redes - OSI model

Created: June 22, 2023 8:49 AM
Updated: November 29, 2023 4:35 PM

Terminology

```
ISP                 - internet service provider; my modem/router has a global ip adress; the global ip address is what makes requests to other servers through the isp; all the devices connected to the modem will get local ip adress and it does that by:
Port number         - after the router knows to what device it should send the data requested (using IP adress), it needs to know what application to send to, and it's when port numbers come into picture; ports are 16 bit numbers; HTTP run on port 80; mongoDB runs on port 2707
sockets             - the interface between a program processes and the internet for example
DNS                 - domain name system; a way of http to find the ip address of a server
Resolved ports      - ports from 0 to 1023; these are ports that are already registered; like HTTP
Mac address         - endereço fisíco da minha placa de rede
IPV4                - 32 bit numbers, 4 words
IPV6                - 128 bit numbers
subnet id           - block of ip adresses. the first 3 words of the ip adress; the last word is the device address, or host id
Ports 1024-49152    - ports registered for applications; like SQL on 1433
Pyhical/wireless    - data is sent either physically through cables(ex. ethernet) or trough wireless(wifi, bluetooth, 3G, 4G, LTE.. )
LAN                 - local area network; computer network that spans a relativaly small geographic are; uses wifi and ethernet
MAN                 - across a city
WAN                 - across countries; tipically uses optical fiber cables
Internet            - is like a collection of LAN, MAN and WAN
Modem/router        - a device used to convert digital signals into analog signals and vice versa
Cookies             - file stored on the client side, on the browser
Thrd party cookies  - cookies for websites that i dont visit

PROTOCOLS:
DHCP                - dynamic host configuration protocol; a set of rules for assigning ip adress
FTP                 - protocol for how files get transfered
HTTP                - hypertext Transfer Protocol. It is an application-layer protocol used for transmitting hypermedia documents, such as HTML files. HTTP uses                         TCP. http is a stateless protocol. the server will not store any information of the client, by default
TCP                 - transmission control protocol. it operates at the transport layer
SMTP                - simple mail transfer protocol
SSH                 - secure shell
VNC                 - virtual network computer. it's for graphical control
UDP                 - user datagram protocol. an alternative to tcp. it's a connection less session. stateless connection
ICMP                - Internet Control Message Protocol. It is a network-layer protocol.primarily used for diagnostic and error reporting purposes in IP networks

```

OSI model

```
OSI                 - open systems interconnection model

LAYERS:
Application         - implemented in software; browsers, messengers..
Presentation        - will get the data from the application layer (words, characters..) and convert into machine binary representation form. enconding and                              encryption also happens here; it also provides abstraction and compression
Session             - authentication
Transport           - UDP and TCP; how data is transfered; it will divide the data into segments and packets
Network             - where the router lives; logical adressing; moving the data source from origin to destination
Data link           - mac address( 12 digit alphanumeric number of the network interface of my computer)
Physical            - physical signal

Packet              - data sent to a server. contains the ip adress of the sender, receiver, and subnet mask

```

TCP/IP model

```
Application
Transport
Network
Data link
Physical

```

![image](https://github.com/andre-diass/my-notes/assets/117690410/173564c6-5bd4-4d96-8978-4a73519da516)
