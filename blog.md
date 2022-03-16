### Template

`Date(s)`

Description of everything that I did and what I learned



---


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
