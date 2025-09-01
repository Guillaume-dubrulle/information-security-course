# X)
- A kill chain is a structured process to engage an adversary, adapted from U.S. military doctrine (F2T2EA: Find, Fix, Track, Target, Engage, Assess).

- Targets computer network intrusions, emphasizing payload development, boundary breach, establishing presence, and achieving objectives.


**Phases of the Intrusion Kill Chain:**

1. **Reconnaissance:** Research and select targets using public sources (websites, mailing lists, social networks).

2. **Weaponization:** Combine malware (e.g., remote access trojan) with exploits into deliverable payloads, often using PDFs or Office files.

3. **Delivery:** Send the payload via email attachments, websites, or USB devices.

4. **Exploitation:** Trigger the code on the victim host, exploiting software vulnerabilities, user behavior, or auto-execution features.

5. **Installation:** Establish persistence by installing backdoors or trojans.

6. **Command & Control:** Compromised hosts connect to a controller server; APT malware often requires manual interaction.

7. **Actions on Objectives:** Intruders achieve goals such as data exfiltration, integrity/availability violations, or lateral movement in the network.

# A)

- **Tactic** = goal → Persistence
- **Technique** =  method → Valid Accounts
- **Subtechnique** = specific method→ Cloud Accounts
- **Procedure** = real-world usage→ APT33 using stolen VPN creds