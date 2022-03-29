Note: This is a work in progress

Connect with me on [LinkedIn](https://www.linkedin.com/in/joe-zurner/)!

# Introduction
My name is Joseph Zurner and I am a cybersecurity student at Harford Community College. I am planning on switching to a four-year university in the fall of 2022, but until then, I will be creating some groundwork to familiarize myself with the field. As of writing this introduction I have some knowledge of cybersecurity, mainly from websites such as TryHackMe and a couple classes I have taken, but my goal is to get ahead and earn some certifications before graduation. This checklist was made to organize my learning path so I know where I stand as well as giving readers a way to follow along. I plan to learn five or more concepts each week but this may change as I am currently busy with college.







# Section 1: The Basics
Before taking on any certifications, I want to get a strong background on some universal topics. These include the basics of networking, penetration testing, tools, and operating systems (namely Windows and Linux). I am familiar with most of these topics, but I want to get a deeper understanding of them.



## 1.1 Resources
- [Practice site 1 (TryHackMe)](https://tryhackme.com/hacktivities)
- [Practice site 2 (PicoCTF)](https://picoctf.org/)
- [Practice site 3 (HackTheBox)](https://www.hackthebox.com/)
- [Practice site 4 (OverTheWire)](https://overthewire.org/wargames/)



## 1.2 Networks
I *think* I gathered all the major components and put them in a logical order. A lot of these will take about a day each, some more and some less:
- [x] IP addresses (IPv4 and IPv6)
- [x] MAC addresses
- [x] DHCP
- [x] ARP
- [x] LAN
- [x] Network topologies
- [x] Packets
- [ ] SMB
- [x] OSI model (overview)
  - [ ] Application layer
  - [ ] Presentation layer
  - [ ] Session layer
  - [ ] Transport layer
  - [ ] Network layer
  - [ ] Data link layer
  - [ ] Physical layer
- [ ] Spanning Tree Protocol
- [x] Encapsulation and de-encapsulation
- [x] Data vs segments/datagrams vs packets vs frames vs bits
- [x] TCP
- [x] UDP
- [ ] Other communication protocols
- [ ] Hardware (router, switch, etc)
- [ ] Physical networking (OSI model 1) (UTP, STP, Coaxial, Fiber Optic Cables)
- [ ] Requests and responses
- [ ] Firewalls
- [ ] IDS and IPS
- [ ] Network Address Translation
- [ ] The internet
- [ ] Web servers and websites
- [ ] Web browsers
- [ ] Cookies
- [x] URLs and DNS
- [ ] HTTP and HTTPS
- [ ] RIP Routing protocol
- [ ] Proxy
- [ ] VPNs
- [ ] Port forwarding
- [ ] VLANs and tagging
- [ ] Subnetting
- [ ] Supernetting

Putting it all together:
- [ ] How does a new device join a network?
- [ ] How do devices communicate on LANs?
- [ ] How do devices communicate on the internet?
- [ ] How are different types of data sent and loaded on your web browser?

Optional topics:
- [x] Subnet masks
- [x] Network classes


## 1.3 Operating Systems: Linux
This will cover commands built into Linux; applications like Wireshark will come later. Many of these are easy enough to cover multiple per day, but others may take longer.

- [ ] File system commands
  - [ ] pwd
  - [ ] ls
  - [ ] cd
  - [ ] mkdir
  - [ ] touch
  - [ ] cat
  - [ ] echo
  - [ ] mv
  - [ ] cp
  - [ ] rm
  - [ ] rmdir
  - [ ] wc
  - [ ] sort
  - [ ] grep
  - [ ] locate
  - [ ] find
  - [ ] file
- [ ] Users and permission commands
  - [ ] su
  - [ ] sudo
  - [ ] useradd
  - [ ] passwd
  - [ ] chmod
  - [ ] chown
- [ ] System information commands
  - [ ] whoami
  - [ ] date
  - [ ] uptime
  - [ ] w
  - [ ] cat /proc/cpuinfo
  - [ ] cat /proc/meminfo
  - [ ] free
  - [ ] du
  - [ ] df
  - [ ] ps/ps aux
  - [ ] top
  - [ ] kill/killall
- [ ] Other basic commands
  - [ ] man
  - [ ] history
  - [ ] clear
  - [ ] apt -get
  - [ ] reboot
- [ ] Networking commands
  - [x] ping
  - [x] traceroute
  - [ ] ip addr
  - [x] whois (domain)
  - [x] dig
  - [ ] wget
  - [ ] curl
  - [ ] ssh
  - [ ] scp
  - [ ] ip address add
  - [ ] ifconfig
  - [ ] netstat
- [ ] Miscellaneous
  - [ ] Shell operators
  - [x] Text editors (VIM, nano)

## 1.4 Common tools
Common add-ons for penetration testing. These will probably take longer than a day.
- [ ] Burp Suite
  - [ ] Burp Intruder
  - [ ] Burp Proxy
  - [ ] Burp Repeater
  - [ ] Burp Target
- [ ] Metasploit
- [ ] Nmap
  - [ ] Nmap automation
- [ ] OpenVPN
- [ ] Nessus
- [ ] fping
- [ ] Dirt Buster
- [ ] John the Ripper
- [ ] hashcat
- [ ] Hydra
- [ ] Wireshark
- [ ] Sublist3r
- [ ] Netcat
- [ ] enum4linux
- [ ] samrump
- [ ] smbclient




# Section 2: The eJPT Certification
The eLearnSecurity Junior Penetration Tester (eJPT) is a certification test graded on performance in penetration tests based on real-world scenarios. It is a more practical alternative to tests such as the CEH or Security+, and I chose this as a starting point because of its hands-on format. For more information, visit the [official website](https://elearnsecurity.com/product/ejpt-certification/).



## 2.1 Resources
- [Collection of resources](https://docs.google.com/document/d/18ix32_14hfPg_kvxiW7aUzog8nZgFA7mu8TVEI_DEgM/edit)
- [Exam information 1](https://infosecwriteups.com/ultimate-guide-to-pass-ejpt-in-the-first-attempt-by-mayur-parmar-75effc877394)
- [Exam information 2](https://elearnsecurity.com/product/ejpt-certification/)
- [Various notes 1](https://github.com/d3m0n4l3x/eJPT)
- [Various notes 2](https://github.com/fdicarlo/eJPT)
- [Various notes 3](https://github.com/hunterluker/eJPT-notes)
