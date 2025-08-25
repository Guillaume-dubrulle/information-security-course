# x)

## Threat modeling
 - What are we working on? (collaboring/data flow diagram)
 - What can go wrong? ([STRIDE](#stride))
 - What are we going to do about it? (Risk management)
 - Did we do a good job? (if would recommend threat modeling then yes)

#### STRIDE
- Spoofing
- Tempering
- Repudiation
- Information Discosure
- Denial of service
- Elevation of privileges

## Infosec scene
### darknetdiaries EP73: WannaCry
- **Date**: May 12, 2017  
  - A massive global ransomware campaign hit organizations across 150 countries.
  - One of the most affected networks: **the NHS (UK’s National Health Service)**.
  - **FireEye**, a cybersecurity company, started analyzing WannaCry.
#### Origin and Spread
- **Shadow Brokers**: a group that hacked the NSA and stole cyber tools/exploits, later releasing them publicly.
  - Among them: **EternalBlue**.
- **EternalBlue**:
  - Exploited a critical vulnerability in **SMB (Windows file sharing)**.
  - Enabled the malware to spread automatically: if one PC was infected,the whole network could be.
- A patch existed, but many systems had not installed it.
- **Windows XP**: no longer supported by Microsoft.
  - Exception: Microsoft released a patch a few days after the attack.
#### The Kill Switch
- WannaCry included a **shutdown mechanism**:
  - It checked the existence of a specific URL.
  - If the URL responded, the ransomware immediately stopped running.
- **Marcus Hutchins**:
  - Found the domain in the code, noticed it was unregistered.
  - Registered the domain himself and made it active.
  - Result: the spread stopped almost instantly worldwide.
  - Marcus became a hero, preventing hundreds of thousands of further infections and **billions in damages**.
#### Impact
- **Infections**: 230,000 computers in 150 countries.
- **Payments**: around 330 victims → $140,000 in Bitcoin.
- **Geopolitical consequences**:
  - First time the EU imposed **sanctions on a country for a cyberattack**.
  - Attribution: **Lazarus Group** (North Korean hackers).

# a) Security hygiene
### For Everyone
- Strong and Unique Passwords
- Multi-factor authantification
- Update the software for potential patch
    - we saw an exemple before with eternal blue
- Double check the mails and files that you download
- Lock your devices expecialy in public
- Don't uses public WIFI without a vpn

### For Companies
Same as for everyone and :
- Train everyone in the companies about theses rules
- Log activities to see if there is something wrong
- Employees must acces to only what they need and not more
- Have a clear way for handling breaches, malware, or ransomware 
    - and test it to make sure it workes

# b) Make-belief boogie-man

## **Threat Model – Taskly (SaaS Project Management Platform)**

### (1) What are we working on?

**Company description:**
Taskly is a company that makes a website to help businesses to stay organized. People use this website to keep track of their to-do lists, share files, and work easily together .

**Key assets (crown jewels):**

1. **Customer database** (projects, tasks, files, user accounts).
2. **API secrets** used for integrations with third-party services (Slack, Google Workspace, Stripe).
3. **Cloud infrastructure** (servers, containers, storage).

**Secondary assets:**

* Application logs, usage statistics, internal employee accounts.

**Customer touchpoints:**

* **Web browser** → **Web app frontend** → **Backend API** → **Cloud database**.
* External service integrations via API.

**System diagram (simplified):**

```
[Client Web Browser] → [WebApp Frontend] → [API Backend] → [Database]
                                     ↘
                                      [External APIs (Slack, Google, Stripe)]
```

---

### (2) What can go wrong? (STRIDE)

**S: Spoofing**

* Pretending to be something or someone other than yourself.

**T: Tampering**

* Modifying something on disk, network, memory, or elsewhere 

**R: Repudiation**

* Claiming that you didn't do something or were not responsible

**I: Information Disclosure**

* Someone obtaining information they are not authorized to access 

**D: Denial of Service**

* Exhausting resources needed to provide service 

**E: Elevation of Privilege**

* Exploiting bugs to escalate privileges and gain admin/root access.

**Prioritization (Probability × Monetary Value):**

1. **Customer data breach (I)** → very high impact (loss of trust, legal issues, GDPR).
2. **Account takeover (S)** → high likelihood (phishing, leaked credentials).
3. **DoS attacks (D)** → direct business continuity risk.

---

### (3) What are we going to do about it?

* **Mitigate**

  * Strong authentication (2FA for exemple).
  * Encrypt data.
  * Centralized logging and monitoring.

* **Eliminate**

  * Remove deprecated API endpoints.
  * Block direct access to the database.

* **Transfer**

  * Cloud provider responsible for physical security and redundancy.

* **Accept**

  * Non-critical usage logs (low sensitivity).

---

### (4) Did we do a good enough job?

* **Regular audits** (secure code reviews, external penetration tests).
* **Continuous monitoring** (SIEM, intrusion detection alerts).
* **Bug bounty program** to detect vulnerabilities in real-world conditions.

# Sources

 - [Threat Modeling](https://www.youtube.com/playlist?list=PLCVhBqLDKoOOZqKt74QI4pbDUnXSQo0nf)
 - [darknetdiaries EP73: WannaCry](https://darknetdiaries.com/transcript/73/)
 - [STRIDE Definition](https://en.wikipedia.org/wiki/STRIDE_model)
 - [OWASP's Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html)
 - [Threat Modeling Process](https://owasp.org/www-community/Threat_Modeling_Process)