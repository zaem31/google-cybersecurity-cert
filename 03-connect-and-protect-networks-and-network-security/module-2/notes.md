# Module 2: Network Operations

## Key Concepts

### Network protocols overview
A **network protocol** is a set of rules used by two or more devices to describe the order and structure of data delivery, basically instructions attached to a data packet telling the receiving device what to do with it. Protocols work like a shared language across every device on the internet. They fall into **3 categories**: communication, management, and security protocols. Security analysts need to know the security implications of protocols too, since some (like DNS) can be exploited to redirect traffic to a malicious site.

### Communication protocols
- **TCP (Transmission Control Protocol)**: connection-based, forms a connection and streams data using a **three-way handshake** (SYN, then SYN/ACK, then ACK). Occurs at the transport layer.
- **UDP (User Datagram Protocol)**: connectionless, faster but less reliable than TCP, good for time-sensitive transmissions like DNS requests. Also transport layer.
- **HTTP**: application layer protocol for client/server communication, uses port 80, considered insecure (plaintext).
- **HTTPS**: the secure version of HTTP, encrypts traffic using SSL/TLS, uses port 443. Application layer.
- **DNS (Domain Name System)**: translates domain names into IP addresses, normally uses UDP port 53 (switches to TCP if the reply is too large). Application layer.

### Management protocols
- **SNMP (Simple Network Management Protocol)**: monitors/manages network devices, can reset passwords, change configs, or report bandwidth usage. Application layer.
- **ICMP (Internet Control Message Protocol)**: reports data transmission errors between devices, commonly used via the "ping" command to troubleshoot connectivity/latency. Internet layer.

### Security protocols
- **HTTPS**: (also listed above) secures HTTP traffic with SSL/TLS encryption.
- **SFTP (Secure File Transfer Protocol)**: securely transfers files using SSH (typically TCP port 22), commonly used with cloud storage uploads/downloads.
- Important limitation: encryption protocols don't hide the source/destination IP address of traffic, so an attacker who intercepts traffic can still learn some basic info even if the content is encrypted.

### Additional network protocols
- **NAT (Network Address Translation)**: lets a router swap a device's private IP address for the router's public IP address (and vice versa for responses), so many devices on a LAN can share one public IP. Spans the internet and transport layers.
- **DHCP (Dynamic Host Configuration Protocol)**: assigns a unique IP address to each device and provides DNS/gateway info, works with the router. DHCP servers use UDP port 67, clients use UDP port 68.
- **ARP (Address Resolution Protocol)**: translates IP addresses into MAC addresses so devices can be found on the local network; each device keeps a cache of known IP-to-MAC matches.
- **Telnet**: connects to a remote system via command line, sends everything in clear text (insecure), uses TCP port 23.
- **SSH (Secure Shell)**: secure alternative to Telnet, encrypted remote connection, uses TCP port 22.
- **POP (Post Office Protocol, mainly POP3)**: retrieves email from a mail server, downloads it locally (doesn't reliably sync across devices). Unencrypted on port 110, encrypted (SSL/TLS) on port 995.
- **IMAP (Internet Message Access Protocol)**: also retrieves email, but keeps mail on the server so it stays synced across multiple devices. Unencrypted on port 143, encrypted on port 993.
- **SMTP (Simple Mail Transfer Protocol)**: sends/routes outgoing email, works with Message Transfer Agent (MTA) software to resolve addresses via DNS. Unencrypted on port 25 (often abused for spam), encrypted (TLS) on port 587.
- Firewalls can filter traffic based on these protocols' port numbers, e.g. only allowing POP3 (port 995) from company IP addresses.

### Wireless security protocols (Wi-Fi / IEEE 802.11)
Wi-Fi (technically IEEE 802.11, maintained by the IEEE) is a family of standards for wireless LAN communication. Wireless security protocols evolved over time to patch vulnerabilities:
- **WEP (1999)**: oldest standard, meant to match wired-level privacy, now considered high-risk and largely phased out, though still seen on old hardware.
- **WPA (2003)**: replaced WEP, used TKIP and larger encryption keys plus a message integrity check to reject tampered transmissions. Still vulnerable to **KRACK attacks** (attacker inserts themselves into the handshake and forces a weak/known encryption key).
- **WPA2 (2004)**: improved on WPA using AES encryption and CCMP (adds message authentication/integrity). Considered today's Wi-Fi security standard, but still technically vulnerable to KRACK. Has **Personal mode** (simple setup, one shared passphrase, good for home use) and **Enterprise mode** (more complex setup, centralized/individualized access control, better for organizations since users never see the actual encryption keys).
- **WPA3 (2018)**: fixes the KRACK vulnerability, uses SAE (Simultaneous Authentication of Equals) for safer key exchange, and increases encryption strength (128-bit, with 192-bit optional in Enterprise mode).

### Firewalls (types and behavior)
- **Hardware firewall**: physical device, inspects packets before they enter the network.
- **Software firewall**: a program on a computer/server rather than a physical device, cheaper but adds processing load to the device it's on.
- **Cloud-based firewall (FaaS)**: hosted by a cloud service provider, filters traffic before it reaches the organization's onsite network, also protects cloud-based assets.
- **Stateful firewall**: tracks information passing through it and proactively flags suspicious behavior, more secure.
- **Stateless firewall**: only follows predefined rules, doesn't track past traffic or spot new suspicious trends, less secure but simpler.
- **NGFW (Next Generation Firewall)**: builds on stateful inspection with deeper features like deep packet inspection, intrusion protection, and (in some cases) live cloud threat-intelligence updates.
- **Port filtering**: a firewall function that blocks/allows specific port numbers to control what traffic is let through.

### VPNs (Virtual Private Networks)
A **VPN** changes your public IP address and hides your virtual location, keeping your data private on networks like the public internet. It encrypts data in transit and uses **encapsulation** (wrapping encrypted data inside another data packet so routers can still read the destination info without exposing the actual content).
- **Remote access VPN**: connects an individual device to a VPN server, commonly used by individuals for personal privacy.
- **Site-to-site VPN**: connects entire networks/locations together, used by enterprises with multiple offices; more complex to configure/manage than remote access VPNs.
- **VPN protocols** (rules for how the secure tunnel is formed):
  - **WireGuard**: newer, high-speed, open-source, simpler to set up/maintain, good for high-bandwidth needs like streaming or large downloads. Works for both site-to-site and remote access.
  - **IPSec**: older, more complex, widely supported across operating systems, extensively tested over time. Commonly used in site-to-site VPNs.
- Organizations increasingly combine VPNs with **SD-WAN (Software-Defined Wide Area Network)**, a virtual WAN service connecting users to applications securely across multiple locations.

### Security zones and segmentation
- **Network segmentation**: dividing a network into segments, each with its own access rules, to contain problems and protect privacy between groups (e.g. separating hotel guest Wi-Fi from staff Wi-Fi).
- **Security zone**: a network segment that protects the internal network from the internet.
  - **Uncontrolled zone**: any network outside the organization's control, e.g. the internet.
  - **Controlled zone**: a protected subnet shielding the internal network from the uncontrolled zone. Includes:
    - **DMZ (demilitarized zone)**: the outer layer, holds public-facing services (web servers, proxy servers, DNS servers, email/file servers that handle external traffic). Acts as a buffer/perimeter for the internal network.
    - **Internal network**: holds private servers/data the organization wants to protect.
    - **Restricted zone**: an even more locked-down zone inside the internal network for highly confidential data, accessible only to employees with specific privileges.
  - Ideally, firewalls separate each of these layers so an attack that gets into the DMZ can't automatically reach the internal network, and one that reaches the internal network can't reach the restricted zone.

### Subnetting and CIDR
- **Subnetting**: dividing one large network into smaller, organized groups called **subnets** (a "network within a network"), improving efficiency and helping create security zones. Devices on the same subnet communicate faster since the switch keeps that traffic local.
- **CIDR (Classless Inter-Domain Routing)**: a method for assigning subnet masks to IP addresses, replacing the older "classful" addressing system that ran out of room as the internet grew. A CIDR address adds a slash and a number (the network prefix) to an IPv4 address, e.g. `198.51.100.0/24`, which represents a defined range of addresses. CIDR reduces routing table size and frees up more usable IPv4 addresses.

### Proxy servers
A **proxy server** sits between clients and external resources/threats, using NAT as part of how it works.
- **Forward proxy**: handles requests from internal clients going out to external resources.
- **Reverse proxy**: handles incoming requests from external systems trying to reach internal services.
- Proxies can also be configured with firewall-like rules, e.g. blocking known malicious websites.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Address Resolution Protocol (ARP) | Determines the MAC address of the next router or device on the path |
| Cloud-based firewalls | Software firewalls hosted by the cloud service provider |
| Controlled zone | A subnet that protects the internal network from the uncontrolled zone |
| Domain Name System (DNS) | Translates internet domain names into IP addresses |
| Encapsulation | A VPN process that protects data by wrapping sensitive data inside other data packets |
| Firewall | A network security device that monitors traffic to or from your network |
| Forward proxy server | A server that regulates and restricts a person's access to the internet |
| HTTP | An application layer protocol providing communication between clients and website servers |
| HTTPS | The secure version of HTTP that provides encrypted communication between clients and servers |
| IEEE 802.11 (Wi-Fi) | A set of standards that define communication for wireless LANs |
| Network protocols | A set of rules devices use to describe the order and structure of data delivery |
| Network segmentation | A security technique that divides the network into segments |
| Port filtering | A firewall function that blocks or allows certain port numbers to limit unwanted communication |
| Proxy server | A server that fulfills client requests by forwarding them to other servers |
| Reverse proxy server | A server that regulates/restricts the internet's access to an internal server |
| SFTP (Secure File Transfer Protocol) | A secure protocol used to transfer files between devices over a network |
| SSH (Secure Shell) | A security protocol used to create a secure connection (shell) with a remote system |
| Security zone | A segment of a network that protects the internal network from the internet |
| SNMP (Simple Network Management Protocol) | Used for monitoring and managing devices on a network |
| Stateful | A firewall class that tracks passing information and proactively filters out threats |
| Stateless | A firewall class that follows predefined rules without tracking prior data packet info |
| Subnetting | The subdivision of a network into logical groups called subnets |
| TCP (Transmission Control Protocol) | An internet communication protocol allowing two devices to form a connection and stream data |
| Uncontrolled zone | The portion of a network outside the organization |
| VPN (Virtual Private Network) | A service that changes your public IP address and masks your virtual location to keep data private |
| WPA (Wi-Fi Protected Access) | A wireless security protocol for devices connecting to the internet |

