For a more readable version, go to [my website](https://josephzurner.com/Blog/).


### Day 0: Setting up

`3/11/22 - 3/13/22`

The 11th through 13th have been my days to set up the learning path and find out what I want to focus on. I plan to start tomorrow so I can have nice weekly sections. Over the coming weeks I will change the checklist as I learn more, but the general idea will stay the same.



---


### Day 1: The Basics of IP Addresses and Subnetting

`3/14/22`

- An IPv4 address is split into four octets, each octet holding an eight-bit value between 0 and 255. The range of IP addresses (IP space) stretches from 0.0.0.0 to 255.255.255.255.
- They are actual two addresses in one, the host address (address of the device) and the network address (address of the network the device is on). Say, for example, an IP address is 172.16.0.1. The first two octets, 172 and 16, refer to the network address while the last two octets, 0 and 1, refer to the host address. All hosts with the same network address are in the same network.
- This isn't consistent, however. When the internet first started, the first octet was the network address while the last three were the host address. Because this wasn't enough, five classes were introduced ranging from A through E. A, B, and C are for devices while D is multicast and E is reserved.
- Class A networks are for large scale networks, working in the same way as the original internet. The first octet is for the network address while the last three are for the host address. The only difference is that the first bit of the network address is fixed to 0. The IP space for class A networks is 0.0.0.0 to 127.255.255.255.
- Class B networks are for medium networks. The first two octets hold the network address while the last two octets hold the host address. The first two bits of the network address are fixed to 10. The IP space for class B networks is 128.0.0.0 to 191.255.255.255.
- Class C networks are small networks. The first three octets are for the network address while the last octet is for the host address. The first three bits of the network address are fixed to 110. The IP space for class C networks is 192.0.0.0 to 223.255.255.255.
- If a device wants to send information to another IP address, it looks at the first bits of the IP address. 0 means class A, 10 means class B, 110 means class C, and so on. If the devices are on the same network, then the sender can send the traffic directly to the destination using the host address. If the devices are on different networks, the traffic is sent to a router in between.
- In 1993, IP addresses started running out again so another new method was introduced called classless interdomain routing, or CIDR. This introduced the idea of a subnet mask. Subnet masks start out the same way as the five class method, where a corresponding subnet mask goes with an IP address. A subnet mask contains only 255s and 0s, with 255s on the left and 0s on the right. If an octet is part of the network address, the subnet mask's corresponding octet will be 255, or all 1s in binary. If an octet is part of the host address, the subnet mask's corresponding octet will be 0, also all 0s in binary.
- This is effectively the same thing as before, which is where subnetting is introduced. For example, say an IP address is 172.16.0.0, which means that the subnet mask would be 255.255.0.0. That gives 65,000 possible IPs, which may be a bit excessive. To better allocate IPs, the subnet mask could be changed to 255.255.255.0, giving 256 subnets.
- CIDR notation makes it easier to write CIDR IP addresses. If an IP in CIDR notation is written as 172.16.1.0 /24, it means the first 24 bits of the subnet mask are active, translating to 255.255.255.0.
- The opposite of subnetting is called supernetting, which means joining a number of small networks together to make a larger network. For example, given the IP address 192.168.0.0 /24 and combining it with 192.168.1.0 /24 will give you 192.168.0.0 /23, a subnet mask of 255.255.254.0.



### Day 2

`3/15/22`

- IPv4 addresses are 32 bits, with each byte representing one of 256 numeric values. IPv6 addresses are 128 bits with every four bytes representing one of 65,535 hexadecimal values. Because there are practically unlimited IP addresses, IPv6 doesn't have classes.
- While both IPv4 and IPv6 can have subnetworks, the term subnet mask is only used for IPv4. Both versions use CIDR notation.
- Public IPs are assigned to the network router by the internet service provider, while private IPs are assigned by the router. Private IPs include 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, and 192.168.0.0 - 192.168.255.255, while public IPs contain every other IP.
- On Linux, you can find your public IP address with the command `curl ifconfig.me` and your private IP with the command `hostname -I`.
- IP addresses don't technically identify hosts; they identify network interfaces. A device with multiple network interfaces will have multiple IP addresses, one for each interface.
- There are over 4 billion IPv4 addresses and over 340 undecillion IPv6 addresses, ensuring we will never run out. In IPv4, about 18 million addresses are reserved for private networks and another 270 million are reserved for multicast addressing.
- While all modern computers and servers include support for IPv6, it still isn't widely deployed in some routers and other hardware.
- Just as IPv4 reserves addresses for private networks, IPv6 has unique local addresses (ULAs) set aside. They are set aside with the routing prefix `fc00::/7`, which is further divided into two /8 blocks with different policies.
- Devices can have an IP address assigned either dynamically or persistently. Persistent configuration is also known as using a static IP address while dynamic configuration is also known as using a dynamic IP address.
- A dynamic IP address means that if a device connects to a network (regardless if it is the first time), it will have a new IP address assigned. Static IP addresses stay the same even if a device leaves and rejoins a network.
- Dynamic addresses are more common and are assigned by a network using dynamic host configuration protocol (DHCP). Addresses assigned with DHCP have a lease and usually an expiration period. If the lease is not renewed before it expires, the address can be reassigned. Some DHCP implementations try to use the same IP addresses for each host based on their MAC address.
- Static addresses are often used in equipment for network infrastructure like routers and mail servers.
- Sticky dynamic addresses are dynamically assigned IP addresses that don't change often, such as when a DHCP service tries to use the same address for repeat MAC addresses.
- DHCP operation has four phases: server discover (discovery), IP lease offer (offer), IP lease request (request), and IP lease acknowledgement (acknowledgement), also known as DORA.
- First, a new device will broadcase a DHCPDISCOVER message on the network, which will be received by the server. Next, the server reserves an IP address for the client and sends a lease offer with a DHCPOFFER message. This message contains a client id (usually the MAC address), the IP being offered, the subnet mask, the lease duration, and the IP address of the server. In response, the client replies with a DHCPREQUEST to request the offered address. When the server receives the DHCPREQUEST, it sends back a DHCPACK to the client including the lease duration and other configuration information.



### Day 3

`3/17/22`

- Each network adapter has a unique MAC address (short for media access control address) assigned by the manufacturer. Similar to IP addresses, if a device has multiple network adapters, it will have multiple MAC addresses.
- MAC addresses are directly tied to the hardware so they will never change, regardless of what network the device is on. Because of their tie to the hardware, they are also called hardware addresses. Windows can call them physical addresses while Apple uses the terms ethernet ID, airport ID, or WiFi address, depending on the communication standard.
- MAC addresses work at the second layer (data link layer) of the OSI model.
- Each MAC address is a 12 digit hexadecimal number displayed with either colons or dashes between every two digits (one octet).
- If a device wants to communicate with another on the same network, it will need the recipient's MAC address. If it knows the IP address of the recipient, it will send out an ARP request.
- An ARP request is a message broadcast to each other device on the local network. Say, for example, computer A wants to find out computer B's MAC address. Computer A will send out a broadcast to all devices on the local network containing its IP address and MAC address as well as computer B's IP address. The message asks what computer owns computer B's IP address and if they can respond with their MAC address.
- When computer B receives the ARP request, it will do two things. First, it looks at its ARP table for an entry with computer A's information. If it can't find one, it will create a new entry with computer A's IP and MAC addresses.
- Second, it will send an ARP reply with its IP and MAC addresses to computer A. Computer A will receive the message and add the information to its own ARP table. This allows computer A to finally send the message to computer B.
- Other versions of ARP include reverse ARP (RARP), which allows devices to find their own IP address; inverse ARP (IARP), which allows a device to find an IP address from a MAC address; proxy ARP, which is a method for ARP requests on other networks through a proxy device; and gratuitous ARP, which is an ARP response that isn't prompted by an ARP request, generally to inform the entire network of updates to its IP or MAC mapping.
- On a Windows device, the ARP table can be seen easily by entering `arp -a` into the command prompt. It will display the internet address (IP address) and the physical address (MAC address) as well as the mapping type (static or dynamic).



### Day 4

`3/18/22`

- The open systems interconnection (OSI) model is used to describe how computers communicate over a network. While it has been replaced with the TCP/IP model, it is still widely used for various reasons.
- The model has seven layers. Each layer describes different interactions in detail. The top layer, layer 7, is where humans can directly interact with computers, while the bottom layer, layer 1, is the raw data transmission over a physical medium. Each other layer is a process involved in turning that raw data into interactable material.
- Layer 7, the application layer, is used by applications on the computer that can be interacted with my the user such as web browsers and email clients.
- Layer 6, the presentation layer, prepares data for the application layer. It coordinates the encoding, encrypting, and compressing of data between two devices. In addition, it prepares data transmitted by the application layer for the session layer.
- Layer 5, the session layer, creates and holds communication channels (sessions) between devices. It opens the sessions, keeps it open and functional while data is being sent, and closes it when the communication is over.
- Layer 4, the transport layer, takes data from the session layer and breaks it into "segments" (or rejoins it when on the receiving end). It also controls the rate at which data is sent and received so both devices work at the same speed, as well as error control.
- Layer 3, the network layer, has two main functions. The first is breaking up segments into network packets (and reassembling the packets on the receiving end), and the second is routing packets by discovering the best route across a physical network. Network addresses, usually IP addresses, are used to route the packets.
- Layer 2, the data link layer, establishes and terminates the connection between two physically-connected nodes on a network. It also breaks packets into frames and sends them onward. There are two main parts, the logical link control (LLC) and media access control (MAC). LLC identifies network protocols, performs error checking, and synchronizes frames while MAC uses MAC addresses to connect devices and define permissions for transmitting and receiving data.
- Layer 1, the physical layer, is responsible for the physical or wireless connection between network nodes. It is responsible for the transmission of the raw 1's and 0's and the bit rate control.
- The transfer control protocol/internet protocol (TCP/IP) is what the modern internet is based on. It is effectively a simplified version of the OSI model.
- Two of the largest changes are the combination of a few layers. The OSI layers 5, 6, and 7 are combined into one application layer, and the layers 1 and 2 are combined into one network access layer.



### Day 5

`3/19/22`

- The TCP/IP model, also known as the internet protocol suite, is a framework using a set of communication protocols for computers to interact. It is named after the TCP and IP protocols.
- A protocol is a set of rules that specify how systems can communicate, in this case how data is transferred from one system to another. This model details how data travels from one computer to another through a series of transformations.
- The four layers of the TCP/IP model are the application layer, transport layer, internet layer, and network interface layer. Each layer contains specific protocols that allows them to transform the data as it passes through.
- The application layer is the closest layer to the user. It contains the protocols used by most applications for providing user services or exchanging application data. Some of the major protocols include HTTP, FTP, SMTP, and DHCP. Data coded according to protocols on this layer are encapsulated intotransport layer protocol units such as TCP streams or UDP datagrams.
- The transport layer establishes basic data channels that applications use for data exchange. Essentially, it tries to provide transportation for data from a process on one device to a process on another device. It determines how much data should be sent where and at what rate as well as ensuring that the data is transmitted without any errors. The main protocol on this layer is TCP (and UDP to a lesser extent), hence the TCP portion of the model's name.
- The internet layer, also known as the network or internetwork layer, routes and delivers packets from source to destination based only on the address. It uses the IP protocol (hence the IP portion of the model's name) which uses IP addrresses to transport packets to the next IP router that has connectivity to a network closer to the final data destination.
- The network interface layer transports bits or packets over a physical medium such as ethernet or wifi.



### Day 6

`3/20/22`

- A computer network is defined as two or more computers connected in a wired or wireless format using cables or WiFi, respectively. A network has the goal of transmitting, exchanging, or sharing data or resources. They are made up of hardware such as routers, switches, and cables as well as software.
- There are a number of network types, usually defined by their size, location, or usage.
- A local area network (LAN) connects computers using wires over a short distance such as an office building or school. They are typically privately owned and relatively easy to work on. A wireless local area network (WLAN) is the wireless version of a LAN.
- A wide area network (WAN) connects computers over a wide area like a country or continent. The internet is an example of a wide area network.
- A metropolitan area network (MAN) is between LANs and WANs in size. As the name suggests, it is usually managed by a city or small countries.
- A personal area network (PAN) is designed to serve one person, generally for the transfer of files between two local devices.
- A storage area network (SAN) is a special network designed to provide access to cloud storage. For the user, it acts as a storage drive that is physically attached to the device.
- A campus area network (CAN), also known as a corporate area network, is between a LAN and MAN in size. It serves places such as entire campuses or large business areas.
- A virtual private network (VPN) uses an encrypted channel between two network end points. It allows a user to access the internet through another device in a secure format.
- When data is sent from one device to another over a network, it contains a header that includes the IP address of the sender and receiver.
- A network is made up of nodes, which are basically the devices making up the network. A node can send, receive, create, or store data and must have an IP address. In essence, a node is any network device that can interact with information from another node. These include computers, printers, routers, etc.
- Nodes are connected with cables, fiber optics, or wireless signals.
- A router is a device that sends information between networks. They analyze data within packets to determine the best way for the information to reach its ultimate destination. They forward data packets until the data reaches its destination.
- A port is a special connection between network devices, identified by a number. They are used to differentiate between different services and protocols and to determine which application, service, or process should receive specific messages.
- The internet is a massive network of billions of devices. Protocols such as HTTP and SMTP allow consistent communication between the devices.
- Internet service providers (ISPs) and network service providers (NSPs) provide the infrastructure that allows the transmission of packets over the internet. They make sure that information goes where its destination is located.
- Peer to peer (P2P) architecture involves two or more computers connected as equals, with no computer having higher power or privileges. Every device on the network acts as a client (a computer accessing a service) and a server (a computer providing services).
- Client/server architecture, also known as a tiered model, involves a central server or group of servers managing resources and providing services to client devices in the network. The clients in the network communicate with each other through the server.
- A network topology is the arrangement of nodes and links in a network. There are a number of topologies but some are more common than others.
- A star topology is laid out so every node on the network is directly connected to a central hub. The central hub is generally the central server in the client/server architecture, providing data transmission between nodes. This type of topology is common because it allows easier management of the entire network. If one node fails, the network will continue unaffected, and devices can be added, removed, and modified without any issues. It also makes it easier to identify errors or performance issues. The entire network is limited by the central hub's ability, and if the central hub goes down, so does the rest of the network.
- A bus topology has all devices connected to a single cable running from one end of the network to the other. It is simple and cost effective, and more nodes can be added easily. If, however, the main cable has any issues, the entire network will fail. This is also hard to troubleshoot and expensive to repair. Bus topologies are best for small networks because more nodes will slow the transmission speed of data.
- A ring topology contains all nodes at some point on a ring. The data can travel in one direction or both, depending on the setup. Only one node can send data at a time which makes it slow but reduces errors. If one node or link fails, then the rest of the network might go down. It is hard to scale a ring topology, and the entire network must be taken down to add, remove, or reconfigure a node. It works well for a small network, but not for larger ones.
- There are many other topologies, but most of them are subsets of those previously mentioned. A couple are unique, such as a tree topology that branches out or a mesh topology, where most nodes are connected to most other nodes.



### Day 7

`3/21/22`

Introductory networking room of THM's complete beginner course

- The OSI model was covered briefly on day 4, but there is a bit more to know.
- As data is passed through each layer of the model (from layer 7 downward), more information is added in the form of headers; this is called encapsulation. Most layers have a header to add.
- Layer 7 adds the application layer header. Right now, the data is just called data.
- Layer 6 adds the presentation layer header.
- Layer 5 adds the session layer header.
- Layer 4 adds the transport layer header, and the data is now called segments or datagrams, depending on whether TCP or UDP is being used.
- Layer 3 adds the network layer header, and the data is now called packets.
- Layer 2 adds the data link header and the data link trailer, and the data is now called frames.
- Layer 1 is now called a data stream, made up of bits.
- When the message is received by another computer, the process is reversed and data is stripped off on each layer. This process is called de-encapsulation.
- Now, back to TCP/IP, TCP is a connection-based protocol, so a stable connection must be made between two computers before any data can be sent. This is called a three-way handshake.
- First, your computer sends a message saying that it wants to form a connection. This request contains a SYN (synchronize) bit, establishing first contact.
- Next, the other computer will respond with a packet containing a SYN bit and an ACK (acknowledgement) bit.
- Lastly, your computer will respond with a packet containing an ACK bit, indicating that the connection has succeeded.
- Any data that is lost or corrupted is re-sent to guarantee a lossless connection.
- Now, to Linux commands. There are a few basic networking commands that are very helpful to know.
- ping: The ping command is very basic, testing if a connection to a remote resource is possible. This could be a website or another device. It uses the ICMP protocol, which is a protocol in TCP/IP; it works on the network layer of the OSI model and the internet layer of the TCP/IP model. The syntax is simply `ping (target)`. It will return the IP address of the target as well as some basic information on the connection.
- traceroute: The traceroute command allows you to see all the nodes that your data goes through on its way to a target. The syntax is the same as ping, just `traceroute (target)`.
- whois: The whois command gives information on a domain, telling a lot about how it is set up. The syntax is `whois (domain)`.
- dig: Dig gives basic information on the DNS setup of a website. The syntax is `dig (domain)`.
