# Module 4: Security Hardening

## Key Concepts

### What security hardening is
**Security hardening** is the process of strengthening a system to reduce its vulnerabilities and **attack surface** (all the potential entry points a threat actor could exploit, like every door/window in a house a burglar could use). It applies to hardware, operating systems, applications, networks, databases, and even physical spaces (cameras, security guards). Common hardening actions: installing patches/updates, tightening configurations (e.g. longer/more frequent password changes, updated encryption standards), removing unused apps/services/ports, and reducing access permissions. Fewer active apps/ports/permissions means less to monitor and fewer weaknesses to exploit.

**Penetration testing (pen test)**: a simulated attack used to find vulnerabilities in a system/network/app/process. Testers document findings in a report, which the security team uses to prioritize and fix issues.

### OS (Operating System) hardening
Since the OS sits between hardware and the user, one insecure OS can put the whole network at risk. Key ongoing tasks:
- **Patch updates**: OS/software updates that fix known security vulnerabilities. Once a vendor publishes a patch, attackers know exactly where the vulnerability is in any system that hasn't updated yet, so patching quickly matters.
- **Baseline configuration (baseline image)**: a documented set of specifications used as a reference point for future builds/releases/updates (e.g. a firewall rule listing allowed/disallowed ports). Security teams compare current settings against the baseline to catch unauthorized changes.
- **Hardware/software disposal**: properly wiping old hardware and removing unused software (unused programs can carry known vulnerabilities even if nobody's using them).
- **Strong password policies**: minimum length/complexity rules, account lockout after repeated failed attempts, and often **MFA (Multi-Factor Authentication)**, verifying identity through 2+ methods (something you know, something you have, something you are).

### Brute force attacks
A **brute force attack** is a trial-and-error method of guessing private info like passwords.
- **Simple brute force attack**: trying random username/password combinations until one works.
- **Dictionary attack**: using a list of commonly used passwords or previously stolen credentials (named for originally using literal dictionary words).

**Testing/assessing vulnerabilities before an attack happens:**
- **Virtual machines (VMs)**: software versions of physical computers, useful for running/testing suspicious code in isolation so it can't affect the rest of the system. Can be wiped and restored to a clean state. Small risk of "VM escape" where malicious code breaks out of the virtual environment.
- **Sandbox environments**: isolated testing environments (physical or virtual/cloud-based) used to test patches, find bugs, evaluate suspicious files, or simulate attacks. Note: some malware is written to detect when it's running inside a VM/sandbox and behaves harmlessly to avoid detection.

**Prevention measures against brute force attacks:**
- **Salting and hashing**: hashing turns data into a unique, one-way (non-reversible) value used to check integrity; salting adds random characters before hashing to make the result more complex/secure.
- **MFA / 2FA**: verifying identity through 2+ factors (2FA specifically uses exactly two).
- **CAPTCHA / reCAPTCHA**: a test proving the user is human, blocking automated brute-force attempts (reCAPTCHA is Google's free version).
- **Password policies**: standardized rules across an organization on complexity, update frequency, reuse limits, and login attempt limits.

### Network hardening
Focuses on network-level protections rather than individual devices.
- **Regularly performed tasks**: firewall rule maintenance, **network log analysis** (examining logs to spot events of interest, usually via a log analyzer or SIEM tool), patch updates, and server backups. A SIEM presents gathered data on a single dashboard (a "single pane of glass") and helps analysts prioritize vulnerabilities from high to low urgency.
- **One-time/setup tasks**: **port filtering** (only allowing ports actually needed by normal operations, disallowing everything else), keeping wireless protocols up to date (disabling older/weaker ones), **network segmentation** (isolating subnets per department or security zone so an issue in one area doesn't spread), and encrypting all network communication with up-to-date standards (restricted zones should get the strongest encryption).

### Layered network security tools (defense in depth)
Adding multiple security layers/tools until the desired security level is reached is called **defense in depth**.
- **Firewall**: allows/blocks traffic based on rules, inspecting packet headers (NGFWs can also inspect payloads). Limitation: can only judge based on header info (unless it's an NGFW).
- **IDS (Intrusion Detection System)**: monitors activity and alerts admins to possible intrusions based on known attack signatures or anomalies. Limitation: can only catch known/obvious attacks and doesn't stop traffic itself, it just alerts. Usually placed behind the firewall to reduce false-positive noise.
- **IPS (Intrusion Prevention System)**: like an IDS, but actively blocks/drops suspicious traffic instead of just alerting. Limitation: it's inline, so if it fails, the connection between the network and the internet can break; also prone to false positives that block legitimate traffic.
- **Full packet capture devices**: record/analyze all network traffic, useful for investigating alerts an IDS raises.
- **SIEM**: aggregates and analyzes log data from firewalls, IDS/IPS, VPNs, proxies, and DNS logs into one dashboard for real-time monitoring. Only reports on issues, it doesn't take action itself.

Each added tool costs money to buy/install/maintain (and sometimes extra staff), so decision-makers weigh cost against risk when choosing a security level.

### Network security in the cloud
Cloud networks need their own hardening, since a CSP hosting the servers doesn't fully prevent intrusions, internal or external threats can still occur. A key difference from traditional hardening: using a **baseline image for cloud server instances** to catch unverified/unauthorized changes. Like OS hardening, cloud data/apps should be separated by function (old vs. new apps, internal vs. front-end systems).

**Key cloud security considerations:**
- **IAM (Identity Access Management)**: manages digital identities and what cloud resources each user can access. Loosely configured user roles are a common risk, since they can let unauthorized users reach critical operations.
- **Configuration**: every cloud service needs precise setup to meet security/compliance standards; misconfiguration is a very common source of breaches, especially during cloud migrations.
- **Attack surface**: every additional cloud service/app adds its own risks, increasing the overall attack surface, though CSPs are generally more scrutinized/secure than typical on-premise setups.
- **Zero-day attacks**: exploits that were previously unknown. CSPs are often quicker to detect/patch these (e.g. patching hypervisors, migrating workloads) than a traditional in-house IT team would be.
- **Visibility and tracking**: organizations can inspect their own traffic in the cloud via flow logs/packet mirroring, but CSPs don't allow customers to monitor traffic on the CSP's own servers directly, CSPs instead rely on third-party audits to prove their security.
- **Pace of change**: CSPs update quickly, so organizations using them may need to adjust their own processes/configurations to keep up.

**Shared responsibility model**: the CSP is responsible for securing the cloud infrastructure itself (data centers, hypervisors, host OS), while the organization using the cloud is responsible for securing their own assets, apps, and configurations running inside it. A common mistake is assuming the CSP is handling something that's actually the customer's responsibility (e.g. configuring an app securely).

### Cloud security hardening techniques
- **IAM**: covered above.
- **Hypervisors**: software that abstracts a host's hardware from the OS environment, letting multiple virtual machines run on one physical machine.
  - **Type 1 hypervisor**: runs directly on hardware (e.g. VMware ESXi), commonly used by CSPs, who manage patching/updates.
  - **Type 2 hypervisor**: runs on top of an existing OS (e.g. VirtualBox).
  - A **VM escape** is an exploit where an attacker breaks out of a VM to access the underlying hypervisor/host or other VMs, a serious risk if the hypervisor is vulnerable or misconfigured.
- **Baselining**: a fixed reference point for how a cloud environment should be configured (e.g. restricting admin portal access, enabling password management/file encryption/threat detection for databases), used to compare against and catch unwanted changes.
- **Cryptography**: securing data via **encryption** (scrambling data into unreadable ciphertext using a key) plus secure key management, protecting data confidentiality/integrity both in the cloud and at rest. Modern encryption security depends on keeping the *key* secret, not the algorithm.
- **Cryptographic erasure (crypto-shredding)**: destroying the encryption key(s) for encrypted data instead of trying to wipe the data itself, since traditional deletion methods are less reliable in the cloud. Once every copy of the key is destroyed, the data becomes permanently undecipherable.
- **Key management tools**: **TPM (Trusted Platform Module)**, a chip that securely stores passwords/certificates/keys, and **CloudHSM (Cloud Hardware Security Module)**, a device that securely stores keys and performs encryption/decryption operations. Customers are generally responsible for their own encryption keys when they provide them, and CSPs have limited ability to help if a customer's own key is lost or compromised. FedRAMP maintains a list of verified CSPs for federal contractors.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Baseline configuration (baseline image) | A documented set of specifications used as a basis for future builds, releases, and updates |
| Hardware | The physical components of a computer |
| Multi-factor authentication (MFA) | A security measure requiring a user to verify identity in two or more ways |
| Network log analysis | The process of examining network logs to identify events of interest |
| Operating system (OS) | The interface between computer hardware and the user |
| Patch update | A software/OS update that addresses security vulnerabilities in a program or product |
| Penetration testing (pen test) | A simulated attack that helps identify vulnerabilities in systems, networks, websites, apps, or processes |
| Security hardening | The process of strengthening a system to reduce its vulnerabilities and attack surface |
| SIEM (Security Information and Event Management) | An application that collects and analyzes log data to monitor critical activities |
| World-writable file | A file that can be altered by anyone in the world |


