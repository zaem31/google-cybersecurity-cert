# Module 3: Introduction to Cybersecurity Tools

## Key Concepts

### Logs and log sources
A **log** is a record of events occurring within an organization's systems/networks. Three common sources:
- **Firewall log**: records attempted/established connections, both incoming traffic from the internet and outbound requests to the internet.
- **Network log**: records all computers/devices entering and leaving the network, plus connections between devices and services.
- **Server log**: records events related to services like websites, email, or file shares, including login, password, and username requests.

### SIEM tools
A **SIEM (Security Information and Event Management)** tool collects and analyzes log data to monitor critical activities. It provides real-time visibility, event monitoring/analysis, automated alerts, and centralized log storage, cutting down how much a person has to manually review. SIEM tools must be configured/customized to match each organization's specific needs and evolving threats.

**Types of SIEM deployment:**
- **Self-hosted**: the organization installs, operates, and maintains the tool on its own infrastructure (managed by internal IT). Ideal when physical control over confidential data is required.
- **Cloud-hosted**: maintained/managed by the vendor and accessed through the internet, good for orgs that don't want to build/maintain their own infrastructure.
- **Cloud-native**: also vendor-managed and internet-accessed, but built specifically to take full advantage of cloud capabilities like availability, flexibility, and scalability.
- **Hybrid**: a mix of self-hosted and cloud-hosted, used to get cloud benefits while keeping physical control over some confidential data.

**Common SIEM tools:**
- **Splunk Enterprise**: self-hosted, retains/analyzes/searches log data and provides real-time alerts.
- **Splunk Cloud**: cloud-hosted, good for hybrid or cloud-only environments.
- **Chronicle (Google)**: cloud-native, retains/analyzes/searches data, built to leverage cloud scalability.

### SIEM dashboards
Dashboards turn raw security data into visual, easy-to-read charts/graphs/tables (similar to how a weather app visualizes temperature/wind data). They help analysts quickly investigate alerts, for example spotting hundreds of login attempts on an account from an unusual location/time and determining the activity is suspicious. Dashboards also surface **metrics**, key technical attributes like response time, availability, and failure rate, that assess performance and can be customized per team/role.

**Splunk dashboards:**
- **Security posture dashboard**: shows the last 24 hours of notable security events/trends for SOC teams; used to check if infrastructure/policies are working as intended.
- **Executive summary dashboard**: tracks overall organizational health over time; used to brief stakeholders with high-level summaries of incidents/trends.
- **Incident review dashboard**: highlights suspicious patterns and higher-risk items needing review, with a visual timeline leading up to an incident.
- **Risk analysis dashboard**: tracks risk per object (a user, computer, or IP address), showing changes in behavior like off-hours logins or unusual traffic, useful for prioritizing mitigation.

**Chronicle dashboards:**
- **Enterprise insights dashboard**: highlights recent alerts and suspicious domain names (indicators of compromise, or IOCs), each with a confidence score and severity level.
- **Data ingestion and health dashboard**: shows event log counts, log sources, and processing success rates, used to confirm logs are properly configured and coming through without error.
- **IOC matches dashboard**: tracks top threats/risks/vulnerabilities by observing domain names, IP addresses, and device IOCs over time to spot trends and prioritize focus.
- **Rule detections dashboard**: shows stats on incidents with the highest occurrence/severity/detections over time, tied to specific detection rules (e.g. flagging a known malicious email attachment).
- **User sign in overview dashboard**: shows user access behavior across the org, useful for catching things like a user signing in from multiple locations at once.

### The future of SIEM tools
As cybersecurity evolves, SIEM tools are moving further into cloud-hosted/cloud-native environments. **SOAR (Security Orchestration, Automation, and Response)** is a collection of applications/tools/workflows that use automation to respond to security events, this frees analysts to focus on more complex, non-automatable incidents. Growth in interconnected IoT (Internet of Things) devices is also expanding the attack surface, and AI/ML is expected to improve SIEM capabilities around detection terminology, visualization, and data storage.

### Open-source vs. proprietary tools
- **Open-source tools**: often free, built collaboratively by the public, and highly customizable. Source code and training material are openly available, letting users modify/improve them. A common myth is that they're less secure than proprietary tools, in reality, wide visibility into the code means issues are often spotted and fixed faster.
  - **Linux**: an open-source operating system (the interface between computer hardware and the user) that can be tailored via a command-line interface. Multiple versions exist for different specific tasks.
  - **Suricata**: open-source network analysis and threat detection software, developed by the Open Information Security Foundation (OISF). Inspects network traffic to flag suspicious behavior and generate logs, and integrates with many SIEM/security tools.
- **Proprietary tools**: owned/developed by a company; users typically pay for use and training, and only the owner can access/modify the source code, so updates depend on the vendor. Usually allow limited customization. Examples: Splunk and Google SecOps (Chronicle).

### Accessibility and security
Security decisions that assume a "typical" user's abilities can fail people with disabilities, for example using color alone (like red) to signal a warning doesn't work for colorblind users. Thinking about accessibility while designing security measures (and getting feedback from a wide range of users) makes protections more effective for everyone, similar to how closed captioning was built for hearing-impaired users but ended up helping a much wider audience.

## New Terms (Glossary)

| Term | Definition |
|------|------------|
| Chronicle | A cloud-native tool designed to retain, analyze, and search data |
| Incident response | An organization's quick attempt to identify an attack, contain the damage, and correct the effects of a breach |
| Log | A record of events that occur within an organization's systems |
| Metrics | Key technical attributes (response time, availability, failure rate) used to assess software performance |
| Operating system (OS) | The interface between computer hardware and the user |
| Playbook | A manual that provides details about any operational action |
| SIEM (Security Information and Event Management) | An application that collects and analyzes log data to monitor critical activities in an organization |
| SOAR (Security Orchestration, Automation, and Response) | A collection of applications, tools, and workflows that use automation to respond to security events |
| Splunk Cloud | A cloud-hosted tool used to collect, search, and monitor log data |
| Splunk Enterprise | A self-hosted tool used to retain, analyze, and search log data and provide real-time alerts |

