# Module 1: Security Domains

## Key Concepts

### The 8 CISSP security domains (revisited in more depth)
Security teams use these domains to organize daily tasks, spot gaps in security, and build their security posture (an organization's ability to manage defense of critical assets/data and react to change).

1. **Security and risk management**: covers security goals/objectives, risk mitigation, compliance, business continuity, and legal/ethical regulations. InfoSec (information security) processes under this domain include incident response, vulnerability management, application security, cloud security, and infrastructure security.
2. **Asset security**: managing storage, maintenance, retention, and destruction of physical/digital assets. Includes creating backups so the organization can recover after an incident.
3. **Security architecture and engineering**: optimizing data security through effective tools/systems/processes. Built on shared responsibility (everyone plays a role in lowering risk) plus principles covered later in the program: threat modeling, least privilege, defense in depth, fail securely, separation of duties, keep it simple, zero trust, and trust but verify.
4. **Communication and network security**: securing physical networks and wireless communication across on-site, remote, and cloud environments, e.g. restricting network access for remote/traveling employees.
5. **Identity and access management (IAM)**: keeping data secure by verifying user identity and authorizing access. Uses the principle of least privilege (granting only the minimum access needed for a task). Four components:
   - *Identification*: proving who you are (username, access card, biometric data)
   - *Authentication*: verifying identity (password, PIN)
   - *Authorization*: access level granted based on role
   - *Accountability*: monitoring/recording user actions (e.g. login attempts)
6. **Security assessment and testing**: security control testing, data collection/analysis, and audits to catch risks before they cause harm. Pen testers are often used here to find exploitable weaknesses.
7. **Security operations**: investigating a breach and implementing preventative measures afterward, using training, reporting/documentation, intrusion detection/prevention, SIEM tools, log management, playbooks, post-breach forensics, and lessons-learned reviews.
8. **Software development security**: using secure coding practices throughout the software development lifecycle (design, development, testing, release) so security isn't an afterthought.

### Threats, risks, and vulnerabilities (definitions and how they differ)
- **Threat**: any circumstance or event that can negatively impact assets (e.g. a social engineering/phishing attempt).
- **Risk**: anything that can affect the confidentiality, integrity, or availability of an asset, basically the likelihood of a threat happening. Simple way to remember it: a risk is being late to work, threats are the traffic, flat tire, or accident that could cause it.
- **Vulnerability**: a weakness that a threat can exploit.
- **Asset risk levels**:
  - *Low risk*: public info (website content, published research), wouldn't harm reputation/finances if exposed.
  - *Medium risk*: non-public info that could cause some damage (e.g. early leak of quarterly earnings).
  - *High risk*: info protected by law/regulation (PII, SPII, intellectual property); severe damage if compromised.
- **Factors affecting risk likelihood**: external risk (outside actors), internal risk (employees/vendors/partners), legacy systems (old, unpatched/unaccounted-for systems), multiparty risk (third-party vendors with access to sensitive IP), and software compliance/licensing gaps.
- **Risk management strategies**: acceptance (accept the risk to avoid disrupting operations), avoidance (plan to avoid it entirely), transference (shift the risk to a third party), and mitigation (lessen its impact).

### Notable real-world vulnerabilities
- **ProxyLogon**: pre-authentication flaw in Microsoft Exchange Server letting an attacker complete authentication remotely to run malicious code.
- **ZeroLogon**: vulnerability in Microsoft's Netlogon authentication protocol (the service that verifies identity before granting access).
- **Log4Shell**: lets attackers run Java code remotely or leak sensitive info by taking control of internet-connected devices.
- **PetitPotam**: affects Windows NTLM, a technique letting a LAN-based attacker trigger an authentication request.
- **Security logging and monitoring failures**: insufficient log/monitoring coverage lets attackers exploit systems undetected.
- **Server-side request forgery**: manipulating a server-side app into accessing/updating backend resources or stealing data.
- As an entry-level analyst, ongoing vulnerability management (monitoring, patching, updating) matters because unapplied patches still leave systems exposed.

### Ransomware and the layers of the web
- **Ransomware**: threat actors encrypt an organization's data, then demand payment for the decryption key to restore access. Negotiations/data leaks often happen through the dark web.
- **3 layers of the web**:
  1. *Surface web*: normal, browser-accessible content most people use.
  2. *Deep web*: requires authorization (e.g. a company intranet).
  3. *Dark web*: only accessible with special software; favored by criminals for its secrecy.

### 3 key impacts of threats, risks, and vulnerabilities
1. **Financial impact**: interrupted production/services, cost of fixing the issue, and regulatory fines.
2. **Identity theft**: exposed PII can be sold/leaked on the dark web.
3. **Reputational damage**: lost customer trust, competitors gaining an edge, legal penalties, and long-term brand damage.

### NIST Risk Management Framework (RMF), 7 steps
1. **Prepare**: activities needed to manage security/privacy risk before a breach happens.
2. **Categorize**: develop risk management processes/tasks based on how confidentiality, integrity, and availability could be impacted.
3. **Select**: choose, customize, and document the controls that protect the organization (e.g. keeping playbooks current).
4. **Implement**: put security/privacy plans into action (e.g. changing password requirements after noticing frequent resets).
5. **Assess**: check whether established controls are actually implemented correctly.
6. **Authorize**: take accountability for the org's security/privacy risks (reports, action plans, milestones).
7. **Monitor**: stay aware of how systems are operating day to day, and flag when changes are needed.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Assess | RMF step 5, determining if controls are implemented correctly |
| Authorize | RMF step 6, accountability for security/privacy risks in an org |
| Business continuity | An org's ability to maintain everyday productivity via disaster recovery plans |
| Categorize | RMF step 2, developing risk management processes and tasks |
| External threat | Anything outside the org with potential to harm its assets |
| Implement | RMF step 4, putting security/privacy plans into action |
| Internal threat | A current/former employee, vendor, or trusted partner who poses a risk |
| Monitor | RMF step 7, staying aware of how systems are operating |
| Prepare | RMF step 1, activities needed to manage risk before a breach occurs |
| Ransomware | A malicious attack encrypting data and demanding payment for access |
| Risk | Anything that can impact the confidentiality, integrity, or availability of an asset |
| Risk mitigation | Having the right procedures/rules in place to quickly reduce impact of a risk |
| Security posture | An org's ability to manage defense of critical assets/data and react to change |
| Select | RMF step 3, choosing/customizing/documenting an org's protective controls |
| Shared responsibility | All individuals in an org taking an active role in lowering risk |
| Social engineering | A manipulation technique exploiting human error for info, access, or valuables |
| Vulnerability | A weakness that can be exploited by a threat |


