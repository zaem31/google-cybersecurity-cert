# Module 1: Network Architecture

## Key Concepts

### What a network is
A **network** is a group of connected devices (laptops, phones, smart devices, workstations, printers, servers) that can communicate over cables or wireless connections. Devices find each other using unique addresses: **IP addresses** and **MAC addresses**.

- **LAN (Local Area Network)**: spans a small area like a home, school, or office building (e.g. your phone connecting to home Wi-Fi).
- **WAN (Wide Area Network)**: spans a large geographic area like a city, state, or country, the internet itself is essentially one giant WAN.

### Core physical network devices
- **Hub**: broadcasts information to every device on the network (like a radio tower), no targeting involved. Less secure since anyone on the network can "hear" all traffic (eavesdropping risk), so mostly used in small setups like home offices now.
- **Switch**: smarter than a hub, sends data only to the intended device by reading its destination MAC address, using a MAC address table to map devices to ports. More secure and better for performance; part of the data link layer.
- **Router**: connects multiple networks together and directs traffic based on the destination IP address (part of the network layer). Can also include firewall features to block malicious traffic.
- **Modem**: connects a router to the internet via an ISP (internet service provider), converting the ISP's incoming signal into a format the local network can use.
- **Firewall**: a security device/feature that monitors and can restrict incoming/outgoing traffic based on rules the organization sets, typically sitting between the trusted internal network and the untrusted outside world (like the internet). It's an important first line of defense, but only one layer among many.
- **Wireless access point**: sends/receives signals over radio waves (Wi-Fi) to create a wireless network, then passes that traffic along to routers/switches.
- **Server**: provides info/services to client devices (the client-server model). Common examples: DNS servers (domain lookups), file servers, mail servers.
- **Virtualization tools**: software that performs the same jobs as physical hubs/switches/routers/modems, offered by cloud providers, giving cost savings and scalability without needing physical hardware.

### Network diagrams
Maps showing the devices on a network and how they connect, using small icons/graphics and dotted lines. Security analysts use them to understand and strengthen the architecture of an organization's private network.

### Cloud networking
- **Cloud computing**: using remote servers, apps, and network services hosted on the internet instead of on local physical devices, this saves money and simplifies operations compared to owning all your own hardware ("on-premise" networking).
- **Cloud network**: a collection of remote servers/computers storing resources/data that's accessed via the internet ("in the cloud" because the company doesn't physically house the servers).
- **CSP (Cloud Service Provider)**: a company (like Google Cloud, AWS, Azure) that owns large data centers and sells storage/compute/networking services, usually accessed through an API or web console.
- **3 categories of cloud services**:
  - **SaaS (Software as a Service)**: ready-to-use software hosted by the CSP.
  - **IaaS (Infrastructure as a Service)**: virtual computing components (servers, storage) a company configures remotely.
  - **PaaS (Platform as a Service)**: tools developers use to build custom applications in the cloud.
- **Hybrid cloud environment**: a mix of on-premise infrastructure plus one CSP's services. **Multi-cloud**: using more than one CSP. Most organizations go hybrid to balance cost savings with control.
- **Software-defined networks (SDNs)**: virtual versions of network devices (virtual switches, routers, firewalls) hosted at a CSP's data center, controlled through software rather than physical hardware.
- **Main benefits of cloud computing/SDNs**: reliability (consistent access with minimal downtime), lower cost (no need to buy/maintain your own hardware), and scalability (pay only for what you use, scale up/down quickly, e.g. spinning up firewalls or intrusion detection quickly when a threat appears).

### How data actually travels: data packets
A **data packet** is the basic unit of info moving across a network, similar to a physical letter: it has a **header** (destination IP/MAC address, protocol info), a **body** (the actual message), and a **footer** (marks the end of the packet).
- **Bandwidth**: amount of data a device receives per second (data quantity ÷ time).
- **Speed**: rate at which packets are received/downloaded.
- Security teams watch bandwidth/speed closely, irregular patterns can signal an attack.
- **Packet sniffing**: the practice of capturing and inspecting data packets moving across a network (used both defensively by analysts and maliciously by attackers).

### The TCP/IP model (4 layers)
A framework for visualizing how data is organized and transmitted, helping security pros pinpoint where in the process a disruption or threat occurred.
1. **Network access layer** (a.k.a. data link layer): creation/transmission of packets, tied to physical hardware (cables, hubs, switches). Includes **ARP (Address Resolution Protocol)**, which maps IP addresses to MAC addresses for local communication.
2. **Internet layer** (a.k.a. network layer): attaches IP addresses to packets and figures out where they need to go, even across different networks. Key protocols: **IP** (routes packets to the right destination) and **ICMP** (reports errors/status, like dropped packets or connectivity issues).
3. **Transport layer**: controls the flow of traffic between two systems. Two main protocols:
   - **TCP (Transmission Control Protocol)**: connection-based, reliable, retransmits lost/corrupted data. Includes port info for the destination service.
   - **UDP (User Datagram Protocol)**: connectionless, faster but less reliable, used for real-time things like video streaming where speed matters more than perfect delivery.
4. **Application layer**: governs how packets interact with the receiving application/user. Common protocols: **HTTP/HTTPS** (web), **SMTP** (email), **SSH** (secure remote access), **FTP** (file transfer), **DNS** (domain name lookups).

**Ports**: within a device's OS, a port is a software-based location that organizes traffic by the type of service being used (e.g. port 25 for email, port 443 for secure web traffic, port 20 for large file transfers), similar to an apartment number telling mail exactly where to go inside a building.

### The OSI model (7 layers)
A more detailed, standardized model of network communication that the 4-layer TCP/IP model is a simplified version of. Working from user-facing down to physical hardware:
7. **Application layer**: direct user-facing processes (web browsing via HTTP/HTTPS, email via SMTP, domain lookups via DNS).
6. **Presentation layer**: data translation/formatting and encryption (e.g. SSL encrypting data for HTTPS websites) so both sending and receiving systems understand the format.
5. **Session layer**: opens/maintains/closes the "session" (connection) between two devices; handles authentication, reconnection, and checkpoints so an interrupted transfer can resume where it left off.
4. **Transport layer**: delivers data between devices, manages transfer speed/flow, and breaks data into smaller segments (**segmentation**) that get reassembled at the destination. TCP and UDP live here.
3. **Network layer**: routes data packets between networks based on IP address info in the packet.
2. **Data link layer**: organizes sending/receiving of packets within a single local network; home to switches and network interface cards. Uses protocols like NCP, HDLC, SDLC.
1. **Physical layer**: the actual physical hardware (hubs, modems, cables), where data ultimately becomes a stream of 0s and 1s sent over the wire.

Different organizations lean on TCP/IP or OSI depending on preference, but analysts should be comfortable with both since they're used interchangeably to communicate about network issues.

### IP addresses and MAC addresses
- **IP address**: a unique string identifying a device's location on the internet, comparable to a mailing address.
  - **IPv4**: written as four numbers (0 to 255) separated by periods, spans 4 bytes, allows about 4.3 billion addresses. Started running out as internet usage grew (IPv4 address exhaustion).
  - **IPv6**: written as eight groups of hexadecimal digits separated by colons, spans 16 bytes, allows for an enormous number of addresses (340 undecillion), created to solve IPv4 exhaustion. Consecutive zero groups can be shortened with `::`.
  - **Public IP address**: assigned by your ISP, shared by every device going out to the internet from your network (like a shared home mailing address).
  - **Private IP address**: only visible to other devices on the same local network, lets devices communicate with each other invisibly to the outside internet.
- **MAC address**: a unique alphanumeric ID assigned to each physical device on a network, used by switches (via a MAC address table) to direct packets to the correct device.

### Inside an IPv4 packet
An IPv4 packet has a **header** (20 to 60 bytes, holds routing info) and a **data section** (up to 65,535 bytes total packet size). Notable header fields: Version, Header Length, Type of Service (priority), Total Length, Identification (for reassembling fragmented packets), Flags/Fragmentation Offset (fragmentation info), **Time to Live (TTL)** (a countdown that prevents packets from looping forever, discarded once it hits zero), Protocol, Header Checksum (detects corruption), Source/Destination IP Address, and Options.

**IPv6 vs. IPv4 differences**: IPv6 has a simpler header (drops fields like Identification/Flags, adds a Flow Label for special handling), offers more efficient routing, and avoids private address collisions that can happen on IPv4 when two devices try to use the same address.

Analyzing these packet fields helps security analysts identify where traffic came from, where it's going, and which protocol it's using, key info for investigating suspicious activity.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Bandwidth | The maximum data transmission capacity over a network, measured in bits per second |
| Cloud computing | Using remote servers, applications, and network services hosted on the internet instead of local physical devices |
| Cloud network | A collection of servers/computers storing resources and data in remote data centers, accessed via the internet |
| Data packet | A basic unit of information that travels from one device to another within a network |
| Hub | A network device that broadcasts information to every device on the network |
| Internet Protocol (IP) | A set of standards for routing and addressing data packets as they travel between devices |
| IP address | A unique string of characters that identifies the location of a device on the internet |
| LAN (Local Area Network) | A network spanning a small area like an office, school, or home |
| MAC address | A unique alphanumeric identifier assigned to each physical device on a network |
| Modem | A device that connects a router to the internet and brings internet access to the LAN |
| Network | A group of connected devices |
| OSI model | A standardized concept describing the seven layers computers use to communicate over a network |
| Packet sniffing | The practice of capturing and inspecting data packets across a network |
| Port | A software-based location that organizes the sending/receiving of data between devices |
| Router | A network device that connects multiple networks together |
| Speed | The rate at which a device sends/receives data, measured in bits per second |
| Switch | A device that connects specific devices on a network by sending and receiving data between them |
| TCP/IP model | A framework for visualizing how data is organized and transmitted across a network |
| TCP (Transmission Control Protocol) | An internet communication protocol allowing two devices to form a connection and stream data |
| UDP (User Datagram Protocol) | A connectionless protocol that doesn't establish a connection before transmitting data |
| WAN (Wide Area Network) | A network spanning a large geographic area like a city, state, or country |


