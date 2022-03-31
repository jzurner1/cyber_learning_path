For a more readable version, go to [my website](https://josephzurner.com/Blog/). This page is just the raw information.


### Day 0: Setting up

`3/11/22 - 3/13/22`

The 11th through 13th have been my days to set up the learning path and find out what I want to focus on. I plan to start tomorrow so I can have nice weekly sections. Over the coming weeks I will change the checklist as I learn more, but the general idea will stay the same.



---


### Day 1

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



### Day 8

`3/22/22`

- VIM is modal, meaning it has different modes. The default mode on opening a file is command mode, which allows you to do commands such as :set number to turn on line numbers.
- Pressing i changes the mode to insert mode, which allows typing. Press Esc to return to command mode.
- In command mode, to quit, do :q. To write to a file, do :w. To write and quit, do :wg. To quit without saving, do :q!.
- To delete lines, enter command mode and move the cursor to a line you want to delete. Press the d key twice.
- To delete a number of lines, type the number of lines then press the d key twice. This will delete the line that your are currently on as well as lines below it, depending on the number entered.
- Press u to undo the last action. Ctrl+r to redo items.
- To search a file, do / and the search string, for example /asdf. Press n to go to the next match and Shift+n to go to the previous match.
- To search and replace, put :%s, the string to replace, another slash, the string to replace it with, and optionally /gc at the end if you want to confirm each replacement. For example, to replace string with STRING, the command would be :%s/string/STRING. To confirm each replacement, it would be :%s/string/STRING/gc.
- To copy a line, put your cursor on it and press yy. To paste it, move your cursor to the line above where you want to place it and press p.
- Bash is a scripting language that runs within Linux terminals. It can be used to achieve complex tasks and automation.
- Bash files either don't have an extension or have the extension .sh.
- The first line of a bash script must always be #!/bin/bash, which tells the computer that it is a bash script.
- Other lines can simply include Linux commands such as echo or pwd.
- To run a bash file, you first need to give it executable permissions. To do this, run chdmod +x yourfile in the terminal, then ./yourfile to run it.
- Like other programming languages, bash lets you assign variables. To create a simple name variable, do name="Bob". Later, the variable can be used with commands in formats like echo $name. When creating variables, make sure there aren't spaces around the equals sign.
- To debug a bash file, run the command bash -x ./yourfile. The program will be run through on the terminal. To debug just parts of a program, add set -x and set +x around the areas you want to debug.
- You can also add parameters to a bash file for inputting outside of the program. To do this, set a variable equal to $1, and when you run the script, add the parameter after it. For example, the code name=$1, echo $name can be run with ./yourfile Bob. The result will be Bob on the terminal, as it was passed in as an argument, set as the name variable, and printed with echo. To add more arguments, do $2, $3, and so on.
- Alternatively, there is an option similar to cin in C++. To read in a value and assign it to a variable, just use the keyword read. For example, to create a variable called name and assign it a user-assigned value, it is simply read name.
- To create an array in bash, it is simply arrayname=('item1' 'item2' 'item3').
- To print all the items in an array, do echo "${arrayname[@]}". The @ means all arguments while the [] specifies that it is an array. To print a single item, replace @ with the item's index position. As with other languages, the index starts at 0.
- To remove an array item, do unset arrayname[item index]. To set an array item, do arrayname[item index]='new item'.
- Bash also has conditional statements. There is no punctuation or brackets at all besides square brackets around the item being tested, such as if [ something ]. The next line would simply be then, the next line what happens, the next line else, the next something else that happens, and the last must be fi.
- Unlike other languages that use operators such as ==, bash uses what looks like flags.



### Day 9

`3/23/22`

- A uniform resource locator (URL), also known as a web address, is a unique identifier for resources on the internet. When typed into an address bar, DNS resolution is used to match it to an IP address and then take you to the website.
- The first part of a URL specifies the protocol needed to access a resource, which is why most URLs begin with http or https. Most of them are then followed by ://.
- The main part of the URL, the domain, includes subdomains, a second-level domain, and a top-level domain, which can be read about below.
- The last major section is the path, which specifies which location to access on the web server. This could be something like /shop/.
- In addition, there may be a query with parameters such as ?=value. On some website such as Wikipedia, there may be a fragment (such as #history) that sets the location on the page.
- All URLs also contain a port which is usually hidden, for example :port80. Ports 80 and 443 are the most common for webservers.
- A top-level domain (TLD) is the ending of the domain, such as .com, .net, or .org.
- There are two types of TLDs, generic TLD (gTLD) and country code TLD (ccTLD). Originally, gTLDs were supposed to indicate the type of organization in charge of the website (such as .gov for a government) and ccTLDs were supposed to indicate geographic area (such as .ca for Canada). There are now over 2000 TLDs due to high demand.
- A second-level domain is the main part of the domain, such as google in google.com. A second-level domain is limited to 63 characters involving a-z, 0-9, and hyphens (not at the beginning or end).
- A subdomain is to the left of a second-level domain, such as admin.google.com. Each subdomain has the same length and character limits as a second-level domain, but multiple subdomains can be attached for a maximum of 253 characters.
- There are multiple types of DNS records. A records resolve to IPv4 addresses; AAAA records resolve to IPv6 addresses; CNAME records resolve to another domain name; MX records resolve to the address of the servers that handle the email for the domain being queried; and TXT records are just plaintext fields.
- You look up a domain in a search bar. Your computer first checks to see if the website is in the local cache, meaning it has been visited recently. If it hasn't, a request is made to your recursive DNS server. Recursive DNS servers are usually hosted by your ISP.
- The recursive DNS server also has a local cache shared by everyone using your ISP. If the website still isn't found, it is sent to the internet's root DNS servers. - - These root DNS servers recognize the TLD in the URL you provided, and you will be referred to the correct TLD server.
- The TLD server contains information on where to find the authoritative server (also known as the nameserver) for your DNS request. The authoritative server is responsible for holding the DNS records for a particular domain name.
- When the DNS record is found, it will be sent back to your device and a copy may be sent to the recursive DNS server where a copy will be saved for future requests. This copy lasts as long as its time-to-live (TTL) value, in seconds.



### Day 10

`3/24/22`

- Metasploit is a framework used by penetration testers for a number of uses. It supports all phases of an engagement from information gathering to post-exploitation.
- There are two main versions, the commercial pro version and the community framework version. The pro version has a graphical user interface (GUI) while the community version is used from the command line.
- The tools available allow for information gathering, scanning, exploit development, post-exploitation, and more.
- After installation, Metasploit can be launched with the command `msfconsole`. This opens the console which will be the main interface for interacting with the different modules provided. Modules are small components built to perform specific tasks.
- An exploit is a piece of code that uses a vulnerability present on the current system. A vulnerability is a design, coding, or logic flag affecting the target system. Exploiting a vulnerability can allow an attacker to gain access to information or execute code on the target system. While an exploit takes advantage of a vulnerability, a payload is used for that exploit to have the desired effect.
- There are a number of categories available. The auxiliary category contains supporting modules such as scanners, crawlers, and fuzzers. Encoders allow encoding exploits and payloads in the hope that a signature-based antivirus solution will miss them. Evasion allows attempts to evade antivirus rather than encoding. The exploit section contains exploits in an organized fashion. NOPs (no operation) do nothing, used as a buffer to achieve consistent payload sizes. Payloads are code that will run on the target system. Post includes modules for post-exploitation.
- There are three different sections under payloads. Singles are self-contained payloads that don't need an additional component to run. Stagers are responsible for setting up a connection between metasploit and the target system. They are useful with staged payloads. Staged payloads first upload a stager on the target system then download the rest of the stage (payload). This is beneficial as it allows larger payloads to be used.
- Once the console is up, the `help` command lists commands and documentation. You can also do `help (command)` for more information about a command.
- The `use` command is used to load a module. After loading a module, the command `show` can be used to learn more and see options. Subcommands include `show all`, `show options`, and `show payloads`, `show targets`, and `show info`, among others.
- The `search` command allows you to search for different modules. You can use `type:` and `platform:` as well as keywords. To see more filters, use `help search`. For example, to find a windows flash exploit, you could do `search type:exploit platform:windows flash`, and your results would come up.
- Once you find a payload/exploit, you can use the command `use` to make it active. Just copy and paste the path to the module after the `use` keyword. Next, do `show options` to see options and `set` to set options. For example, to set SSL to yes, do `set SSL yes`. After choosing settings, just enter `exploit` to run the command.
- To return to the main console, use the command `back`.
- While modules are usually stored in `/usr/share/metasploit-framework/modules`, mine are stored at `/opt/metasploit-framework/embedded/framework/modules`.
- Within the modules folder is six folders, one for each type of module: exploits, payloads, auxiliary, encoders, post, and NOPs.
- Exploit modules are usually used for exploitation. They were created to allow you to take advantage of an exploit or a vulnerability. Within the exploits folder is another group of folders for every major operating system or piece of software that has an exploit, such as Windows and Firefox.
- Payloads are files that are left on an exploited system that give the attacker access or control over the system. Some versions are called rootkits. The payloads folder contains singles, stagers, and stages, which were explained above.
- Auxiliary contains unique attacks such as DoS, fuzzers, and scanners.
- Encoders simply re-encode payloads and exploits to get past security systems. The encoders folder has a number of subcategories such as php, cmd, and more.
- The NOP folder contains things that make the computer do nothing for a clock cycle. The subcategories are similar to encoders.
- Post covers post exploitation, usable after the system has been exploited. They provide extra pieces of functionality such as keyloggers or camera viewers.



### Day 11

`3/26/22`

- back simply returns to the previous menu
- banner displays a random Metasploit banner
- cd works the same as the normal terminal, allowing you to change directories
- color enables or disables colors
- connect is basically a mini Netcat clone, allowing you to connect to remote hosts
- edit allows you to edit the current module in Vim
- exit will exit msfconsole
- grep is the same as normal Linux, returning matches from a command
- help is the same as well
- info is very helpful as it provides information about modules including options, targets, and more
- irb allows you to create Metasploit scripts in a live Ruby shell
- jobs lets you see jobs, which are modules running in the background
- kill will simply kill any running jobs when matched with a job ID
- load loads a plugin from Metasploit's plugin directory
- loadpath will load a "third-part module tree for the path", whatever that means
- unload will unload a previously loaded plugin
- resource runs resource/batch files that can be loaded through msfconsole
- route allows you to route sockets through a session to allow some pivoting capabilities
- search lets you search for modules with regex; there are a number of filters that can be used
- sessions lets you list, interact with, and kill spawned sessions such as shells
- set allows you to set framework options and parameters for the current module
- unset is the opposite of set
- setg lets you set global variables
- show lists all modules within Metasploit, can be followed up with the type (like exploits)
- use lets you use a module that you have selected by adding the path
- Exploits in Metasploit are all either active or passive
- Active exploits will exploit a specific host, run until completion, and then exit
- Passive exploits wait for incoming hosts and exploit them as they connect. They generally focus on clients such as web browsers or FTP clients
- To use an exploit, the first step is to find one that you want to use. This can be done with the search command or show
- Once an exploit is chosen, it must be selected with the use command and the path relative to the exploit folder, such as use exploit/windows/smb/ms09_050_smb2_negotiate_func_index
- Selecting an exploit with the use command opens up a couple more commands, namely exploit (starts the exploitation attempt) and check



### Day 12

`3/27/22`

- TCP and UDP are two methods for data to move between devices.
- TCP (transmission control protocol) is connection oriented, meaning that once a connection is established, data can be transmitted in both directions. To establish a connection, a three-way handshake must be completed. In addition, TCP uses retransmission error detection to make sure that the data received is the correct data. If it isn't, it is send again.
- UDP (user datagram protocol) is connectionless, meaning each piece of data can be send separately and doesn't need to be together. It uses checksums for data integrity, but otherwise is very bare. This makes it faster than TCP but less reliable.
- Checksums are small blocks of data that have different values for different data. This ensures that if the data is changed even a little bit, the checksum will be different, showing that it may need to be retransmitted.
- Connection oriented means that there must be a solid connection between the devices before data can be sent, but once there is, it can be sent either way.
- Connectionless indicates that data, even in the same transmission, doesn't have to be attached to itself and can be sent individually.
- Retransmission is the resending of packets that are damaged or lost.



### Day 13

`3/29/22`

- When data leaves one device to travel to another, it goes through a process called encapsulation as it travels through the OSI model. When it enters the other device, it goes through the de-encapsulation process.
- The data is just called data in the OSI model application, presentation, and session layers.
- The transport layer adds a segment header to the data, and it is then called segments or datagrams.
- The network layer adds a packet header, and it is then called packets.
- The data-link layer adds both a frame header and a frame trailer, and it is now called frames.
- The physical layer converts the data into bits.
- The process is reversed in de-encapsulation, starting with bits and ending with data.
- All the forms of data can be represented in a sort of grid, 32 bits wide by however many bytes tall.

**TCP Segments:**
- The first 16 bits contain the source (client) port number
- The second 16 bits contain the destination (server) port number
- The entire second row contains the sequence number, used to guarantee that the packets are sent in order.
- The entire third row contains the acknowledgement number, basically the byte number that the destination expects to receive next; used to make sure all packets are received.
- The first 4 bits of the fourth row contains the data offset, indicating how far the data is from the beginning of the segment.
- The next 3 bits are reserved, all set to zero.
- The next 9 bits are for various flags: NS, CWR, ECE, URG, ACK, PSH, RST, SYN, and FIN.
- The last 16 bits of the fourth row indicate the receive window, which is the number of bytes the sender of the segment is willing to receive. This is part of TCP flow control.
- The first 16 bits of the fifth row contains the checksum used for error checking.
- The last 16 bits contains the urgent pointer, used for priority data. Associated with the URG flag.
- The last section is options, containing 0 to 320 bits of data. It must be divisible by 32, so any difference must have padding. These options can indicate a number of things but aren't used too often.

**UDP Datagrams:**
- If data is sent with UDP instead of TCP, it will be a datagram at the transport layer instead of a segment.
- Datagrams are a lot smaller, with only a few sections.
- The first 16 bits contain the source (client) port number, same as TCP
- The second 16 bits contain the destination (server) port number, also the same
- The first 16 bits of the second row contains the length (in bytes) of the header, always between 8 and 65,636 bytes. Using jumbograms in IPv6, it is possible to have longer datagrams.
- The second 16 bits of the second row holds the checksum, which is optional in IPv4 and mandatory in IPv6. If it isn't used, it will hold all 0s.
- The data is contained in the third row and beyond.

**IPv4 Packets:**
- The first four bits contain the version, which is always 0100 (4 in binary).
- The second four bits contain the header length field, which indicates how long the header is, measured in 32 bit units called words. The values range from 5 words (160 bits/20 bytes) to 15 words (480 bits/60 bytes). This is used to show where the header ends and the data starts, also known as the data offset. It will always be 5 words long unless there are options present, which is not common.
- Bits 8-15 contain the type of service (TOS). TOS is used to manage bandwidth by priority, with some actions given higher priority than others. If it is not enabled, bandwidth is managed on a first come, first served basis.
- The last 16 bits of the first row contains the total length of the packet, including the header and the data. This is measured in bytes instead of words. The size ranges from 20 bytes (20 in the header, 0 for data) to 65,535 bytes. In IPv4, if required, some packets can be broken down into smaller sizes to get through some areas. This is called fragmentation; they are reassembled at the other end.
- The first half of the second row contains the packet's identification, also known as the fragment ID. This is used in the event of fragmentation, identifying what fragment of a larger packet this is.
- The next three bits are flags related to fragmentation. The first is always zero; the second is the don't fragment (DF) flag, preventing it from being fragmented and instead dropping it if it can't travel through a network; the third is the more fragments (MF) flag, indicating that there are more fragments coming after this one.
- The last 13 bits of the second row contains the fragment offset. It is used in reassembling fragmented packets. It is used to indicate the starting position of the data in the fragment in relation to the start of the data in the original packet.
- The first 8 bits of the third row indicates the time-to-live (TTL). It used to mean the maximum number of seconds that a packet can survive, but it has come to mean the number of hops across a router or switch that are allowed. It is made to prevent a packet being around forever.
- The next 8 bits of the third row contains the protocol field, defining the type of data in the data portion of the packet. It is indicated with protocol numbers. Some common protocol numbers include 1 for ICMP, 6 for TCP, and 17 for UDP.
- The second half of the third row is the header checksum. This is used to verify that the data hasn't been corrupted at all, but occasionally a few errors will cancel each other out.
- The entire fourth row contains the source address, meaning the IPv4 address of the sender.
- The entire fifth row contains the destination address, meaning the IPv4 address of the recipient.
- The next section, for options, is rarely used. If it is, it contains anywhere from 0 to 40 bytes of options. It will be padded with 0's to maintain a length divisible by 32 bits/4 bytes.

**IPv6 Packets**
- The first four bits contain the version, similar to IPv4 packets. These, for obvious reasons, contain the value 0110 (6 in binary).
- The next 8 bits contain the traffic class, similar to the TOS in IPv4 packets.
- The last 20 bits contain the flow label, indicating to intermediate devices that a packet belongs to a specific stream of packets between a source and destination.
- The first 16 bits of the second row contains the payload length, indicating the length of the data portion in bytes. This does not include the header length.
- The next 8 bits of the second row is the Next Header, specifying the protocol used such as TCP, UDP, or ICMPv6. It also uses values to indicate the protocol like the protocol field in IPv4. These values are indicated in hex.
- The last 8 bits is the hop limit, similar to the TTL in IPv4 but more accurately named.
- The source and destination addresses are the same as in IPv4 but now they each take up 128 bits instead of 32 bits.
