# Module 2: Security Frameworks and Controls

## Key Concepts

### Frameworks vs. controls
- **Security frameworks**: guidelines for building plans to mitigate risk/threats to data and privacy. Support compliance with laws and regulations (e.g. healthcare uses frameworks to comply with HIPAA).
- **Security controls**: safeguards designed to reduce specific security risks, used alongside frameworks (e.g. requiring MFA to access medical records is a control supporting HIPAA compliance).
- 3 common control types: **encryption** (converting data from readable plaintext to unreadable ciphertext, protects confidentiality), **authentication** (verifying who someone is, e.g. username/password, or MFA with a code or biometrics like fingerprint/voice/face scan), and **authorization** (granting access to specific resources once identity is confirmed).
- **Vishing**: a social engineering attack that exploits voice communication to steal sensitive info or impersonate someone, this is one way biometrics like voice can be exploited.

### Specific frameworks
- **Cyber Threat Framework (CTF)**: developed by the U.S. government to give cybersecurity professionals a common language for describing/sharing cyber threat activity, helping orgs respond faster to evolving threats.
- **ISO/IEC 27001**: internationally recognized framework (part of the ISO 27000 family) for managing security of assets like financial data, intellectual property, and employee/third-party info. Outlines requirements for an information security management system and best practices, but doesn't mandate specific controls, just provides a collection organizations can choose from.

### Control categories
Controls can be physical, technical, or administrative, and are used to prevent, detect, or correct security issues.
- **Physical controls**: gates, fences, locks, security guards, CCTV/surveillance, access cards/badges.
- **Technical controls**: firewalls, MFA, antivirus software.
- **Administrative controls**: separation of duties, authorization, asset classification.

### The CIA triad (applied more deeply)
- **Confidentiality**: only authorized users access specific data; strengthened by the principle of least privilege (limiting access to only what's needed for the job).
- **Integrity**: data is verifiably correct, authentic, and reliable; supported by cryptography (transforming data so unauthorized parties can't read/tamper with it) and encryption.
- **Availability**: data is accessible to authorized users when needed, without being over-exposed to people who don't need it.
- Example: a bank needs confidentiality (protecting financial info), integrity (flagging suspicious spending pattern changes), and availability (letting customers reliably access their accounts) all at once.

### NIST Cybersecurity Framework (NIST CSF)
Voluntary framework of standards, guidelines, and best practices for managing cybersecurity risk, usable by for-profit, nonprofit, and government organizations. Built around 5 core functions:
1. **Identify**: manage cybersecurity risk and its effect on people/assets (e.g. monitoring internal network devices for issues).
2. **Protect**: implement policies, procedures, training, and tools to mitigate threats (e.g. updating processes after studying past incidents).
3. **Detect**: identify potential incidents and improve monitoring speed/efficiency (e.g. tuning a tool to correctly flag low/medium/high risk).
4. **Respond**: use proper procedures to contain, neutralize, and analyze incidents, then improve the process afterward.
5. **Recover**: restore affected systems/data/assets back to normal operation after an incident.

*(Note: some later course material expands this to 6 functions by adding "Govern," which covers establishing/overseeing/improving an org's overall cybersecurity strategy and risk processes.)*

**NIST SP 800-53**: a related, more specific framework providing a unified set of security controls for protecting federal government information systems (including private companies building systems for federal use), used to help maintain the CIA triad for those systems.

### OWASP security principles
Guidelines used alongside NIST frameworks and the CIA triad to reduce threats/risks:
1. **Minimize attack surface area**: reduce potential entry points (attack vectors, like phishing emails or weak passwords) a threat actor could exploit, e.g. disabling unused features, restricting access, requiring stronger passwords.
2. **Principle of least privilege**: give users only the access needed for their tasks, limiting the damage if their credentials are compromised.
3. **Defense in depth**: use multiple, layered security controls (MFA, firewalls, IDS, permissions) so an attacker has to get through several barriers.
4. **Separation of duties**: no one person should hold enough privilege to misuse the system alone (e.g. the person who signs paychecks shouldn't also prepare them).
5. **Keep security simple**: avoid overly complex controls, they become unmanageable and hurt collaboration.
6. **Fix security issues correctly**: when an incident happens, quickly find the root cause, contain it, identify the vulnerability, and test that the fix actually works.
7. **Establish secure defaults**: the most secure state should be the default state; it should take extra effort to make something insecure.
8. **Fail securely**: when a control fails, it should default to the safest option (e.g. a broken firewall should block everything, not let everything through).
9. **Don't trust services (third parties) blindly**: don't assume a partner/vendor's systems are secure just because they say so, verify independently.
10. **Avoid security by obscurity**: a system's security shouldn't depend on keeping its inner workings secret; it should hold up through real safeguards like strong password policies, defense in depth, and audit controls.

### Security audits
- **Security audit**: a review of an org's security controls, policies, and procedures against a set of expectations, checking both internal criteria (policies, procedures, best practices) and external criteria (laws, regulatory compliance).
- **Two types**: external and internal, entry-level analysts are more likely to help with internal audits.
- **Purpose**: protect data, avoid fines/penalties, and identify gaps for remediation and growth. Audit frequency depends on local laws and compliance regulations.
- **Factors that shape what audits an org runs**: industry type, org size, ties to government regulation, geographic location, and voluntary compliance decisions.
- **5 common elements of an internal audit**:
  1. **Establish scope and goals**: scope identifies the people, assets, policies, procedures, and technologies involved; goals outline what the org wants to achieve (e.g. implementing NIST CSF functions, strengthening controls).
  2. **Conduct a risk assessment**: identify potential threats/risks/vulnerabilities to figure out what security measures need attention.
  3. **Complete a controls assessment**: review existing assets and classify controls as administrative, technical, or physical to check they're actually effective.
  4. **Assess compliance**: confirm the org is meeting relevant regulations (e.g. GDPR, PCI DSS depending on where/how the business operates).
  5. **Communicate results**: summarize scope/goals, list risks and urgency, note compliance gaps, and give recommendations to stakeholders.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Asset | An item perceived as having value to an organization |
| Attack vectors | The pathways attackers use to penetrate security defenses |
| Authentication | The process of verifying who someone is |
| Authorization | Granting access to specific resources in a system |
| Availability | Data is accessible to those who are authorized to access it |
| Biometrics | Unique physical characteristics used to verify identity |
| Confidentiality | Only authorized users can access specific assets or data |
| CIA triad | Model that helps inform how organizations consider risk in systems/policies |
| Detect | NIST core function: identifying incidents and improving monitoring speed/efficiency |
| Encryption | Converting data from a readable format to an encoded format |
| Govern | NIST core function: overseeing and improving cybersecurity strategy/policy alignment with business goals |
| Identify | NIST core function: managing cybersecurity risk and its effect on people/assets |
| Integrity | Data is correct, authentic, and reliable |
| NIST CSF | Voluntary framework of standards/guidelines/best practices for managing cybersecurity risk |
| NIST SP 800-53 | Unified framework for protecting information systems in the U.S. federal government |
| OWASP | Nonprofit focused on improving software security |
| Protect | NIST core function: policies, procedures, training, and tools that mitigate threats |
| Recover | NIST core function: returning affected systems back to normal operation |
| Respond | NIST core function: containing, neutralizing, and analyzing incidents, then improving processes |
| Risk | Anything that can impact confidentiality, integrity, or availability of an asset |
| Security audit | A review of an org's security controls, policies, and procedures against expectations |
| Security controls | Safeguards designed to reduce specific security risks |
| Security frameworks | Guidelines for building plans to mitigate risk/threats to data and privacy |
| Security posture | An org's ability to manage defense of critical assets/data and react to change |
| Threat | Any circumstance or event that can negatively impact assets |


