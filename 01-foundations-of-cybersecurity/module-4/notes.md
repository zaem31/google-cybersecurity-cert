# Module 4: Foundations of Cybersecurity: Cybersecurity Tools and Programming Languages

## Key Concepts

### Logs
A **log** is a record of events happening inside an organization's systems (e.g. someone signing into a computer, or accessing a web service). Logs are the raw data source that most security tools organize and analyze to catch vulnerabilities or breaches.

### SIEM tools (Security Information and Event Management)
- Collects and analyzes log data in real time so analysts don't have to manually read through pages of logs.
- Surfaces alerts for specific types of risk instead of making the analyst find everything manually.
- Displays data through dashboards, which vary by tool and by what a specific user has access to.
- Can be **on-premise** or **cloud-hosted**. Cloud-hosted tends to be easier to set up/maintain, so less experienced teams often lean that way.
- Common examples: **Splunk Enterprise** (self-hosted) and **Google Chronicle** (cloud-native).

### Network protocol analyzers (packet sniffers)
Capture and analyze the data traffic moving through a network, essentially keeping a record of everything a computer on the network encounters. Common tools: **tcpdump** and **Wireshark**.

### Playbooks
A **playbook** is a manual documenting the exact steps to take for a specific operational task (e.g. responding to an incident). Playbooks differ by organization, but the goal is always the same: guide an analyst through a consistent, repeatable process.

Two important playbooks for forensic work:
- **Chain of custody playbook**: documents who has possession of evidence and when, throughout an investigation. Every time evidence changes hands, it must be logged so its location/integrity can always be verified.
- **Protecting and preserving evidence playbook**: covers how to safely handle fragile/volatile digital evidence. Uses the **order of volatility**, a sequence for which data must be preserved first (prioritizing data that would be lost if a device is powered off). Mishandled evidence can become unusable, so the first priority is always to preserve/copy the data before investigating.

### Programming languages & operating systems used by analysts
- **Programming** lets analysts automate repetitive tasks with more accuracy and less human error than doing them manually.
- **Linux**: an open-source (publicly available) operating system. Not a programming language itself, but relies on a command-line interface (text-based commands) rather than a GUI like macOS/Windows. Commonly used by analysts to review logs and investigate things like unusual network traffic.
- **SQL (Structured Query Language)**: used to create, interact with, and query a **database** (an organized collection of information, sometimes with millions of individual **data points**). Lets analysts filter huge datasets down to exactly what they need.
- **Python**: used for repetitive, detail-heavy tasks that benefit from automation and consistency.
- **Automation**: using technology to cut down manual/repetitive effort and reduce the risk of human error, which is the main reason security teams rely on programming.

### Other tools and concepts
- **Web vulnerability**: a flaw in a web app that a threat actor could exploit for unauthorized access, data theft, or malware deployment. The OWASP Top 10 is a reference list of the most critical web app risks.
- **Antivirus software (anti-malware)**: prevents, detects, and removes malware/viruses, often by scanning a device's memory for known malware patterns.
- **Intrusion Detection System (IDS)**: monitors system activity and flags possible intrusions by scanning network packets (small chunks of data moving through a network), which makes it easier to catch threats early.
- **Encryption**: converts readable data (plaintext) into unreadable, encoded data (ciphertext) so only authorized users can read it. Its goal is confidentiality. Different from encoding, which uses a public conversion method just to let systems share data, not to keep it secret.
- **Penetration testing (pen testing)**: simulating an attack on systems/networks/apps to find vulnerabilities before a real attacker does. Considered a thorough risk assessment covering both external and internal threats.

### Building a cybersecurity portfolio
A portfolio goes beyond a resume, it shows actual work: education, skills, and hands-on proof of what you can do. Ways to host one:
1. **Documents folder** (local hard drive) — simple but not easily shareable online.
2. **Google Drive / Dropbox** — cloud storage with easy sharing and automatic updates.
3. **Google Sites** — a built website with a shareable URL, good for a polished public-facing portfolio.
4. **Git repository** (GitHub, GitLab, Bitbucket) — store documents, labs, and screenshots from each course; this is exactly what this repo is for.

Portfolio project ideas suggested by the course: a professional statement, a security audit, network structure/security analysis, Linux file-permission practice, SQL query filtering, vulnerability identification for a small business, an incident handler's journal, text file parsing, and a resume.


## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Antivirus software | Software used to prevent, detect, and eliminate malware and viruses |
| Database | An organized collection of information or data |
| Data point | A specific piece of information |
| Intrusion Detection System (IDS) | An application that monitors system activity and alerts on possible intrusions |
| Linux | An open-source operating system |
| Log | A record of events that occur within an organization's systems |
| Network protocol analyzer (packet sniffer) | A tool that captures and analyzes data traffic within a network |
| Order of volatility | The sequence outlining which data must be preserved first, from most to least volatile |
| Programming | Creating a specific set of instructions for a computer to execute tasks |
| Protecting and preserving evidence | The process of properly working with fragile, volatile digital evidence |
| SIEM (Security Information and Event Management) | An application that collects and analyzes log data to monitor critical activities |
| SQL (Structured Query Language) | A language used to create, interact with, and request information from a database |

