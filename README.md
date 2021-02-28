# netwhat
an introduction to network problematics



Networks connect devices

the goal of the network is to move information from one device to another

to share information, they must speak the same language -> protocols (instructions of how to handle the information)

◦ #What is an IP address

[What is an IP Address – Definition and Explanation](https://www.kaspersky.com/resource-center/definitions/what-is-an-ip-address)

An IP (Internet Protocol) address is a **unique address** that identifies a **device** on the internet or a **local network**.

In essence, IP addresses are the **identifier** that **allows information to be sent between devices on a network**: they contain location information and make devices accessible for communication. The internet needs a way to differentiate between different computers, routers, and websites. IP addresses provide a way of doing so and form an essential part of how the internet works.

An IP address is a *string of numbers separated by periods*. IP addresses are expressed as a set of four numbers — an example address might be 192.158.1.38. Each number in the set can *range from 0 to 255*. So, the full IP addressing range goes from 0.0.0.0 to 255.255.255.255.

*IP addresses are not random*. They are mathematically produced and allocated by the Internet Assigned Numbers Authority (IANA), a division of the Internet Corporation for Assigned Names and Numbers (ICANN). ICANN is a non-profit organization that was established in the United States in 1998 to help maintain the security of the internet and allow it to be usable by all. Each time anyone registers a domain on the internet, they go through a domain name registrar, who pays a small fee to ICANN to register the domain.

[video](https://www.youtube.com/watch?v=LIzTo6e4FgY)

[IPV4 32 bits](https://www.youtube.com/watch?v=EDAnsWpOjGM)

---.---.---.---
each part has 8 bits (1 byte)

192.168.0.1 = 11000000.10101000.00000000.00000001

so the maximum value is 255 = 11111111
and the minumiu is 0 = 00000000
(256 possible combinations)
But in the host section there is a catch. We **cannot** use the *firts* or *last* IP address, these are reserved. The first is the network address and the last is a broadcast address, used to send messages to all computers in the network. So we only have 254 usable host in a netmask like *255.255.255.0*.

◦ #What is a Netmask

A subnet mask is always *paired* with an *IP* adress and is used to *identify* the **network section** and the **host section** of the address.

In its *simplest form* whenever you see *255* this is the *network* part of the address, whenever you see a *0* this is the *host* part os the address. The real way to see wich part is wich, is by looking at the subnet mask binary bits and compating it to the IP address **binary bits**. Anytime you see a **1** value, this bit is the network section anytime you see a **0**, it's the host section.

To be able to look at an IP adress and know wich class it belongs to, the easiest way is to memorize the first octet.

But instead of a full subnet mask, we often see it written as an forward slash and then the number od Network bits.

192.54.103.29 with the netmask 255.255.255.0 = *192.54.103.29/24*

looking to the host part *29* (binary **00011101**), remember the firts (*192.54.103.0*) is the network address and the last (*192.54.103.255*) is a broadcast address.

◦ #What is the subnet of an IP with Netmask

A 32-bit IP address uniquely identifies a single device on an IP network. The 32 binary bits are divided into the host and network sections by the subnet mask but they are also broken into four 8-bit octets.

◦ #What is the broadcast address of a subnet

[What is a broadcast address and how does it work?](https://www.ionos.com/digitalguide/server/know-how/broadcast-address/)

Broadcasting in a computer network is transmitting a message which **does not require a response** to *all users* of the *network*.

One computer in a network sends a data packet to all other users at the same time. The sender does not need to indicate recipient addresses – this is how the broadcast process differs from unicast, where only a single known recipient is addressed. The general advantage of broadcasting is that information can be distributed without having to be transmitted multiple times.

A special address is required to carry out the procedure, which replaces the recipient addresses in question. This broadcast IP is of particular use if the addresses of the individual network users are not known.

The broadcast address of a subnet is the last combination of the host bit's, reserved for send messages to all devices in the same networ (broadcast).

◦ #What are the different ways to represent an ip address with the Netmask



◦ #What are the differences between public and private IPs
◦ #What is a class of IP addresses

| Class | Adresseses | Bits Network (**n**) Host (*h*) | Networks| Hosts
| --- | --- |
| A | 0.0.0.1 - 126.255.255.255| **n**.*h*.*h*.*h* | 126 (2^7 -2*) | 16.777.214 (2^24 - 2*) 
| B | 128.0.0.0 - 191.255.255.255| **n**.**n**.*h*.*h* | 16.382 (2^14 -2*) | 65.534 (2^16 - 2*) 
| C | 128.0.0.0 - 191.255.255.255| **n**.**n**.**n**.*h* | 2.097.150 (2^21 -2*) | 254 (2^8 - 2*) 
| D | 224.0.0.0 - 239.255.255.255| - | - | Multicast 
| E | 240.0.0.0 - 255.255.255.254| - | - | experimental tests 
*firts IP:network last IP:broadcast

◦ #What is TCP
◦ #What is UDP
◦ #What are the network layers
◦ #What is the OSI model
◦ #What is a DHCP server and the DHCP protocol
◦ #What is a DNS server and the DNS protocol
◦ #What are the rules to make 2 devices communicate using IP addresses
◦ #How does routing work with IP
◦ #What is a default gateway for routing
◦ #What is a port from an IP point of view and what is it used for when connecting
to another device
