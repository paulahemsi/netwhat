# netwhat
an introduction to network problematics

* [What is an IP address](#what_is_an_IP_address)
* [What is a Netmask](#what_is_a_Netmask)
* [What is the subnet of an IP with Netmask](#what_is_the_subnet_of_an_IP_with_Netmask)
* [What is the broadcast address of a subnet](#what_is_the_broadcast_address_of_a_subnet)
* [What are the different ways to represent an ip address with the Netmask](#what_are_the_different_ways_to_represent_an_ip_address_with_the_Netmask)
* [What are the differences between public and private IPs](#what_are_the_differences_between_public_and_private_IPs)
* [What is a class of IP addresses](#what_is_a_class_of_IP_addresses)
* [What is TCP](#what_is_TCP)
* [What is UDP](#what_is_UDP)
* [What are the network layers](#what_are_the_network_layers)
* [What is the OSI model](#what_is_the_OSI_model)
* [What is a DHCP server and the DHCP protocol](#what_is_a_DHCP_server_and_the_DHCP_protocol)
* [What is a DNS server and the DNS protocol](#what_is_a_DNS_server_and_the_DNS_protocol)
* [What are the rules to make 2 devices communicate using IP addresses](#what_are_the_rules_to_make_2_devices_communicate_using_IP_addresses)
* [How does routing work with IP](#how_does_routing_work_with_IP)
* [What is a default gateway for routing](#what_is_a_default_gateway_for_routing)
* [What is a port from an IP point of view and what is it used for when connecting to another device](#what_is_a_port_from_an_IP_point_of_view_and_what_is_it_used_for_when_connecting_to_another_device)



Networks connect devices

the goal of the network is to move information from one device to another

to share information, they must speak the same language -> protocols (instructions of how to handle the information)

## What_is_an_IP_address

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

The Internet protocol version 4 (**IPv4**) defines an IP address as a **32-bit** number. Due to the *increasing need* for and using up of available IPv4 addresses, a new IP version (**IPv6**) with **128** bits for the IP address was developed in 1995. It became a standard in December 1998. In July 2017, a final definition of the protocol was published. The IPv6 application has been running since the middle of the 2000s.

## What_is_a_Netmask

A subnet mask is always *paired* with an *IP* adress and is used to *identify* the **network section** and the **host section** of the address.

In its *simplest form* whenever you see *255* this is the *network* part of the address, whenever you see a *0* this is the *host* part os the address. The real way to see wich part is wich, is by looking at the subnet mask binary bits and compating it to the IP address **binary bits**. Anytime you see a **1** value, this bit is the network section anytime you see a **0**, it's the host section.

To be able to look at an IP adress and know wich class it belongs to, the easiest way is to memorize the first octet.

But instead of a full subnet mask, we often see it written as an forward slash and then the number od Network bits.

192.54.103.29 with the netmask 255.255.255.0 = *192.54.103.29/24*

looking to the host part *29* (binary **00011101**), remember the firts (*192.54.103.0*) is the network address and the last (*192.54.103.255*) is a broadcast address.

## What_is_the_subnet_of_an_IP_with_Netmask

A 32-bit IP address uniquely identifies a single device on an IP network. The 32 binary bits are divided into the host and network sections by the subnet mask but they are also broken into four 8-bit octets.

## What_is_the_broadcast_address_of_a_subnet

[What is a broadcast address and how does it work?](https://www.ionos.com/digitalguide/server/know-how/broadcast-address/)

The broadcast address of a subnet is the last combination of the host bit's, reserved for send messages to all devices in the same network (broadcast).

Broadcasting in a computer network is transmitting a message which **does not require a response** to *all users* of the *network*.

One computer in a network sends a data packet to all other users at the same time. The sender does not need to indicate recipient addresses – this is how the broadcast process differs from unicast, where only a single known recipient is addressed. The general advantage of broadcasting is that information can be distributed without having to be transmitted multiple times.

A special address is required to carry out the procedure, which replaces the recipient addresses in question. This broadcast IP is of particular use if the addresses of the individual network users are not known.

The sender initiates the broadcast connection and provides the address at which the recipients can contact them. A broadcast works in a similar way to a mailing list: the recipients are not visible to each other and the sender has no way of knowing the addresses of the network users. Only if the users contact the sender one-to-one do they disclose their own address.

Each network or subnet has a dedicated broadcast address, through which **all users** of the network can *broadcast*.

In a broadcast address, *all the host bits are set to the binary value 1*, so if all host bits are set to the value 0, this is the subnet address.

Example: IPv4 address 192.128.64.7/24

192.128.64.7 is the IP address and 24 is the subnet mask. The **/24** *corresponds* to the subnet mask **255.255.255.0**. The IP address consists of 4 decimals – called octets – which are separated by points. One octet contains 8 bits, which is why IPv4 is a 32-bit address. Each octet can represent a number between 0 and 255. In this case, the **whole of the last octet consists of host bits**. Therefore, in this example, the broadcast address would be *192.128.64.255* – so all host bits at *1*.

Where can you find the broadcast address? The IP address is a 4-digit series of numbers with values from 0 to 255. A *broadcast IP address* is only **assigned once** in each network. It is **always** the *last IP address of the subnet*.


## What_are_the_different_ways_to_represent_an_ip_address_with_the_Netmask

In IPv4 there are three default subnet masks corresponding to the three classes of IP addresses. 
There are currently *three ways* of showing the subnet masks for IPv4 addresses: 
you can show them in dotted decimal, binary, or classless interdomain routing (CIDR). 

**Dotted decimal** consists of a string of decimal numbers, using the full stop (dot) as a separation character, as in **127.0.0.1**.

The **binary** notation for a *Class A* default mask would look like **11111111.00000000.00000000.00000000**.

The **CIDR** (Classless Inter-Domain Routing) notation uses a slash/then the number of *bits that need to be turned on in the mask*. So for a *Class A* it would be **/8**, for *Class B* it would be **/16**, and finally for a *Class C* it would be **/24**.

[subnet-mask](https://www.sciencedirect.com/topics/computer-science/subnet-mask)

## What_are_the_differences_between_public_and_private_IPs

[about public and privete IPs](https://help.keenetic.com/hc/en-us/articles/213965789-What-is-the-difference-between-a-public-and-private-IP-address-)

All IPv4 addresses can be divided into two major groups: **global** (or public, external) - this group can also be called *'WAN addresses'* — those that are used on the Internet, and **private** (or local, internal) addresses — those that are used in the *local network* (LAN).

These are **public** (global) addresses that are **used on the Internet**. 
A public IP address is an IP address that is used to access the Internet. Public IP addresses can be routed on the Internet, unlike private addresses. 

The presence of a public IP address on your router or computer will allow you to organize your own server (VPN, FTP, WEB, etc.), remote access to your computer, video surveillance cameras, and get access to them from anywhere on the global network.

With a public IP address, you can set up any home server to publish it on the Internet: Web (HTTP), VPN (PPTP/IPSec/OpenVPN, WireGuard), media (audio/video), FTP, NAS, game server, etc.

Private (internal) addresses are not routed on the Internet and no traffic can be sent to them from the Internet, they only supposed to work within the local network.

Internet Assigned Numbers Authority (IANA) is the organization responsible for registering IP address ranges to organizations and Internet Service Providers (ISPs). To allow organizations to freely assign private IP addresses, the Network Information Center (InterNIC) has reserved certain address blocks for private use. The following IP blocks are reserved for private IP addresses.

Private addresses include IP addresses from the following subnets:

|				Range					|  Network 		|	Mask 		 		| Hosts			|
|:--------------------------------------| :-------:		| :-------------------:	| ---------:	|
| from 10.0.0.0 to 10.255.255.255 		| 10.0.0.0		|	255.0.0.0 or /8 	|  16.777.216	|
| from 172.16.0.0 to 172.31.255.255		| 172.16.0.0	|	255.240.0.0 or /12	|  1.048.576	|
| from 192.168.0.0 to 192.168.255.255	| 192.168.0.0	|	255.255.0.0 or /16	|  65.536		|

And a special range recommended according to rfc6598 for use as an address pool for CGN (Carrier-Grade NAT)

|				Range					|		Mask 		 	|
|:--------------------------------------| -------------------:	|
| from 100.64.0.0 to 100.127.255.255 	|	255.192.0.0 or /10 	|

Those are reserved IP addresses. These addresses are intended for use in *closed local area networks* and the allocation of such addresses is not globally controlled by anyone.

Direct *access* to the *Internet* from a private IP address is *not possible*. In this case, the connection to the Internet must go through **NAT** (Network Address Translation replaces the private IP address with a public one). Private IP addresses within the same local network must be *unique* and cannot duplicate.

As far as Internet security is concerned, the use of a **private** IP address is **more secure** than the use of a public IP address, as private IP addresses are **not directly visible** on the Internet and are located behind *NAT*, which also ensures the security of the home network. When using a public IP address, measures are required to provide additional security for the computer or server that are exposing their services to the Internet

## What_is_a_class_of_IP_addresses

| Class | Adresseses                  | Bits Network (**n**) Host (*h*) | Networks            | Hosts                   |
|:----- | :--------------------------:| :-----------------------------: | :-----------------: | -----------------------:|
|  A    | 0.0.0.1 - 126.255.255.255   | **n**.*h*.*h*.*h*               | 126 (2^7 -2*)       | 16.777.214 (2^24 - 2*)  |
| B     | 128.0.0.0 - 191.255.255.255 | **n**.**n**.*h*.*h*             | 16.382 (2^14 -2*)   | 65.534 (2^16 - 2*)      |
| C     | 128.0.0.0 - 191.255.255.255 | **n**.**n**.**n**.*h*           | 2.097.150 (2^21 -2*)| 254 (2^8 - 2*)          |
| D     | 224.0.0.0 - 239.255.255.255 | -                               | -                   | Multicast               |
| E     | 240.0.0.0 - 255.255.255.254 | -                               | -                   | experimental tests      |

*firts IP:network last IP:broadcast*

## What_is_TCP

[wikipedia](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)

The Transmission Control Protocol (TCP) is one of the main protocols of the Internet protocol suite. It originated in the initial network implementation in which it complemented the Internet Protocol (IP). Therefore, the entire suite is commonly referred to as TCP/IP. TCP provides reliable, ordered, and error-checked delivery of a stream of octets (bytes) between applications running on hosts communicating via an IP network. Major internet applications such as the World Wide Web, email, remote administration, and file transfer rely on TCP, which is part of the Transport Layer of the TCP/IP suite. SSL/TLS often runs on top of TCP.

## What_is_UDP

## What_are_the_network_layers

## What_is_the_OSI_model

## What_is_a_DHCP_server_and_the_DHCP_protocol

## What_is_a_DNS_server_and_the_DNS_protocol

## What_are_the_rules_to_make_2_devices_communicate_using_IP_addresses

## How_does_routing_work_with_IP

## What_is_a_default_gateway_for_routing

## What_is_a_port_from_an_IP_point_of_view_and_what_is_it_used_for_when_connecting_to_another_device

