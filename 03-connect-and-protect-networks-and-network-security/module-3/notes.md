# Module 3: Secure Against Network Intrusions

## Key Concepts

### Why networks need protecting
Networks are constantly at risk from malware, spoofing, packet sniffing, and traffic-flooding attacks. A single successful attack can leak confidential data, damage an organization's reputation/customer trust, and cost significant time and money to fix. Real example: the **2014 Home Depot breach**, hackers infected servers with malware and stole credit/debit card info for over 56 million customers before the attack was shut down.

### Backdoor attacks
A **backdoor** is a weakness intentionally left in a system (usually by a developer/admin for troubleshooting or admin purposes) that bypasses normal access controls. Attackers can also install their own backdoor after compromising a system to keep persistent access. Once inside through a backdoor, an attacker can install malware, launch a DoS attack, steal data, or weaken other security settings.

### Impact categories of network attacks
1. **Financial**: lost revenue from downtime, cost of rebuilding infrastructure, potential ransomware payments, and litigation/settlement costs if customer data is exposed.
2. **Reputational**: public loss of trust once a breach becomes known, customers may switch to competitors.
3. **Public safety**: attacks on government/critical infrastructure (power grids, water systems, military comms) can put the physical safety of the public at risk.

### Denial of Service (DoS) and Distributed Denial of Service (DDoS)
- **DoS attack**: floods a network/server with traffic to disrupt normal operations, the goal is simply to overload something until it crashes or can't respond to legitimate users.
- **DDoS attack**: a DoS attack that uses multiple devices/servers across different locations at once to flood the target, making it more likely to overwhelm the system.
- **Botnet**: a collection of malware-infected computers controlled by a single attacker (the "bot-herder"), often used to carry out DDoS attacks by having every infected device send traffic to a target at the same time.
- **3 common network-level DoS attacks**:
  1. **SYN flood attack**: exploits the TCP three-way handshake (SYN → SYN/ACK → ACK) by flooding a server with SYN requests, if the number of requests exceeds available ports, the server becomes overwhelmed.
  2. **ICMP flood attack**: repeatedly sends ICMP request packets, forcing the server to keep responding until bandwidth is used up and the server crashes.
  3. **Ping of death**: sends a single oversized ICMP packet (over 64KB, the max size for a properly formed packet), overloading and crashing a vulnerable system.
- **Real-world example**: on October 21, 2016, a botnet built by a group of university students (originally meant to target gaming servers, then leaked publicly) was used by other attackers to send tens of millions of DNS requests to a major DNS service provider, taking down access to many major websites across North America and Europe for about two hours before service was restored.

### Packet sniffing (malicious use)
**Packet sniffing** is the practice of using software/hardware tools to observe or capture data packets as they move across a network, security analysts use it legitimately for investigation/debugging, but attackers use it to steal information.
- **Passive packet sniffing**: reading data packets in transit without altering them (like a mail carrier secretly reading your mail before delivering it).
- **Active packet sniffing**: manipulating packets in transit, e.g. redirecting them to the wrong port or changing their contents.
- **How devices normally filter traffic**: a device's **NIC (Network Interface Card)** normally only accepts packets addressed to its own MAC address. Attackers can set a NIC to **promiscuous mode**, where it accepts all traffic on the network, even packets not meant for it, this is what makes sniffing tools like Wireshark effective.
- **Ways to defend against packet sniffing**: use a VPN to encrypt traffic, make sure sites use HTTPS (SSL/TLS encryption), and avoid unprotected/unencrypted public Wi-Fi (or use a VPN if you must).

### IP spoofing and related attacks
**IP spoofing**: changing a data packet's source IP address to impersonate an authorized system, so the traffic looks trustworthy and can get past firewall rules meant to block outside traffic.
- **On-path attack** (also called a meddler-in-the-middle attack): the attacker places themselves between two devices with a trusted relationship and intercepts/alters the data (e.g. stealing login credentials, or spoofing a DNS response to redirect a domain to a malicious IP). Best defense: encrypt data in transit (e.g. TLS).
- **Replay attack**: the attacker captures a legitimate data transmission and delays or resends it later, either causing connection issues or impersonating the original authorized user.
- **Smurf attack**: combines IP spoofing with a DoS technique, the attacker spoofs a user's IP, floods it with ICMP packets, and the flood hits the broadcast address so it's sent to every device on the network, overwhelming and shutting things down. Best defense: an advanced firewall (like an NGFW) that can detect abnormal broadcast traffic.
- **Firewall defense against IP spoofing**: configure firewalls to reject any incoming traffic claiming to have the same IP address as the internal/local network, since legitimate devices with that address should already be inside.
- **Defense in depth reminder**: no single strategy stops every attack type, layering multiple defenses (encryption, firewalls, monitoring) gives the strongest protection.

### Network protocol analyzers (packet sniffing tools)
A **network protocol analyzer** (a.k.a. packet sniffer/packet analyzer) captures and analyzes network traffic, commonly used to investigate suspicious activity. Common tools: SolarWinds NetFlow Traffic Analyzer, ManageEngine OpManager, Azure Network Watcher, Wireshark, and **tcpdump**.
- **tcpdump**: a lightweight, command-line, open-source (built on libpcap) tool, text-based, preinstalled on many Linux distributions, also works on macOS and other Unix-based systems.
- **What a tcpdump output shows**: timestamp, source IP, source port, destination IP, and destination port for each captured packet. By default it tries to resolve IPs to hostnames and ports to their common service names.
- **Common uses**: establishing a baseline for normal network traffic, detecting malicious traffic, setting up custom alerts, and finding unauthorized devices/access points. Downside: attackers can use the same tools to capture sensitive info like usernames and passwords if traffic isn't encrypted.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Active packet sniffing | A type of attack where data packets are manipulated in transit |
| Botnet | A collection of malware-infected computers controlled by a single threat actor (the "bot-herder") |
| Denial of service (DoS) attack | An attack that targets a network or server and floods it with network traffic |
| Distributed denial of service (DDoS) attack | A DoS attack using multiple devices/servers in different locations to flood a target |
| ICMP (Internet Control Message Protocol) | An internet protocol used by devices to report data transmission errors |
| ICMP flood | A DoS attack performed by repeatedly sending ICMP request packets to a network server |
| IP spoofing | Changing the source IP of a data packet to impersonate an authorized system |
| On-path attack | An attack where a malicious actor places themselves between two devices and intercepts/alters data in transit |
| Packet sniffing | The practice of capturing and inspecting data packets across a network |
| Passive packet sniffing | A type of attack where an actor connects to a network hub and observes all traffic without altering it |
| Ping of death | A DoS attack caused by sending an oversized ICMP packet (over 64KB) |
| Replay attack | A network attack where a data packet is intercepted and delayed or repeated at a later time |
| Smurf attack | A network attack combining IP spoofing with a flood of ICMP packets sent to an authorized user's IP |
| SYN flood attack | A DoS attack that simulates a TCP connection and floods a server with SYN packets |


