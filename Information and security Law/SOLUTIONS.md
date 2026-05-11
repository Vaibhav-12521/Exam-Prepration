# INFORMATION SECURITY & CYBER LAW — PROBLEM SET SOLUTIONS
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6002 | **Semester:** VI

---

## ====== PROBLEM SET I — UNIT 1: Basic Concepts of Technology and Law ======

### Q1. What is Cyber Security?
**Cyber Security** is the practice of protecting computer systems, networks, programs, and data from digital attacks, unauthorized access, damage, or theft. It involves implementing technologies, processes, and security controls to defend against cyber threats.

**Key Goals (CIA Triad):**
- **Confidentiality** – data only accessible to authorized users
- **Integrity** – data not altered/tampered
- **Availability** – data accessible when needed

**Components:**
- Network security, Endpoint security, Application security
- Identity & Access Management
- Risk management & Incident response
- Security awareness training

**Exam Tip:** Always start with definition, then mention CIA Triad, then list components.

---

### Q2. What is Cybercrime?
**Cybercrime** refers to criminal activities that are carried out using a computer, network, or the Internet. It can target individuals, organizations, or governments.

**Categories:**
1. **Crimes against individuals** – cyberstalking, phishing, identity theft
2. **Crimes against property** – hacking, virus attacks, IPR theft
3. **Crimes against government** – cyber terrorism, cyber warfare
4. **Crimes against society** – online gambling, child pornography

**Examples:** Hacking, phishing, DDoS, ransomware, identity theft, cyberstalking, online fraud, data breach.

**Exam Tip:** Categorize, then give examples in each category.

---

### Q3. Various Software Attacks
1. **Virus** – malicious code that replicates by attaching to other programs
2. **Worm** – self-replicating malware that spreads through networks
3. **Trojan Horse** – malware disguised as legitimate software
4. **Spyware** – secretly gathers user information
5. **Adware** – displays unwanted ads
6. **Ransomware** – encrypts files; demands payment for decryption
7. **Rootkit** – hides malicious activity at OS level
8. **Keylogger** – records keystrokes
9. **Logic Bomb** – triggers under specific conditions
10. **Backdoor** – bypasses normal authentication
11. **Bot/Botnet** – compromised computers controlled remotely
12. **Scareware** – tricks users into installing fake software

**Exam Tip:** Memorize at least 5–6 types with one-line definition each.

---

### Q4. Layers of Security (Defense in Depth)
**Defense in Depth** is the layered security approach using multiple controls:

| Layer | Examples |
|-------|----------|
| **1. Physical Security** | Locks, guards, biometrics, CCTV |
| **2. Perimeter Security** | Firewalls, DMZ, IDS/IPS |
| **3. Network Security** | VPNs, NAC, network segmentation |
| **4. Endpoint Security** | Antivirus, EDR, host firewalls |
| **5. Application Security** | Secure coding, OWASP, WAF |
| **6. Data Security** | Encryption, DLP, backups |
| **7. Identity & Access Management** | MFA, RBAC, SSO |
| **8. Operational Security** | Policies, procedures, awareness |
| **9. Disaster Recovery / BCP** | Backup sites, recovery plans |

**Why layers?** If one layer fails, others provide protection. No single control is foolproof.

---

### Q5. Cyber Attack vs Cyber Threat

| Cyber Threat | Cyber Attack |
|--------------|--------------|
| **Possibility** of an unwanted incident | **Actual attempt** to exploit/damage |
| Potential, not yet realized | Realized event |
| Identified through risk assessment | Identified through monitoring/SIEM |
| Example: malware exists in wild | Example: malware has infected system |
| Defended via controls | Detected via incident response |

**Cyber Threat:** Any condition or event that may compromise security (e.g., known vulnerabilities, threat actors).
**Cyber Attack:** A deliberate, malicious action by an attacker (hacking, phishing, DDoS).

**Relationship:** Threat → Vulnerability → Attack → Damage

---

### Q6. Active Attacks
**Active attacks** involve **modification of data** or creation of false data — they affect system operation.

**Types:**
1. **Masquerade** – one entity pretending to be another (impersonation)
2. **Replay Attack** – capture and resend valid messages
3. **Modification of Messages** – altering content in transit
4. **Denial of Service (DoS / DDoS)** – preventing legitimate access
5. **Repudiation** – sender denies having sent message

**Difference from Passive Attacks:**
- Passive: only **observation** (eavesdropping, traffic analysis) – hard to detect, easy to prevent (encryption)
- Active: **modification** – hard to prevent, easier to detect

**Exam Tip:** Always contrast with passive attacks.

---

### Q7. Harmful Acts in Cyber Security
1. **Hacking** & unauthorized access
2. **Phishing** and spear-phishing
3. **Identity Theft**
4. **Cyberstalking** and cyber bullying
5. **Spreading Malware** (virus, ransomware)
6. **Data Breach** / data theft
7. **DDoS attacks**
8. **Online Financial Fraud** (UPI scams, banking fraud)
9. **Social Engineering**
10. **Cyber Espionage**
11. **Child pornography & online abuse**
12. **Cryptocurrency scams**

---

### Q8. Advanced Cybercrimes in India
1. **UPI / Banking Fraud** – fake payment links
2. **Phishing Scams** – fake bank/SBI/IRCTC messages
3. **Aadhaar Misuse** & identity theft
4. **Online Matrimonial Fraud** – fake profiles to extort money
5. **Cyberstalking** on social media
6. **Cryptocurrency Scams** & Ponzi schemes
7. **Deepfake-based Extortion** – AI-generated fake videos
8. **SIM-swap Fraud** – telecom-based banking attacks
9. **Cyberterrorism** – attacks on power grids, critical infra
10. **Ransomware** on hospitals, govt offices (e.g., AIIMS Delhi 2022)
11. **OTP Fraud** – social engineering for OTPs
12. **Sextortion** – blackmail via intimate images

**Famous incidents:** AIIMS Delhi ransomware (2022), Cosmos Bank attack (2018), Aadhaar leaks.

---

### Q9. Cyber Terrorism
**Cyber Terrorism** is the politically-motivated use of computers and information technology to cause **severe disruption or widespread fear** in a society.

**Goals:**
- Intimidate population
- Coerce government
- Advance political/ideological agenda

**Targets:**
- Critical infrastructure (power grids, water, transport)
- Financial systems (banks, stock markets)
- Government databases
- Defense systems

**Examples:**
- Attack on Ukrainian power grid (2015)
- Mumbai 26/11 attackers used VoIP
- Attacks on Iran's nuclear facilities (Stuxnet)

**Indian Law:** **Section 66F of IT Act 2000** deals with cyber terrorism. Punishment: **life imprisonment**.

**Difference from cybercrime:** Cybercrime is for personal/financial gain; cyber terrorism is politically motivated mass terror.

---

### Q10. Cyber Warfare
**Cyber Warfare** refers to **politically-motivated cyber attacks by nation-states** (or state-sponsored actors) against another nation's infrastructure, data, or systems with intent to cause damage, disruption, or espionage.

**Components:**
1. **Espionage** – intelligence gathering (e.g., spying on diplomats)
2. **Sabotage** – damaging infrastructure (Stuxnet)
3. **Propaganda** – information warfare, fake news
4. **Disruption** – disabling services

**Famous Examples:**
- **Stuxnet (2010)** – US-Israel attack on Iran's nuclear centrifuges
- **NotPetya (2017)** – Russian attack on Ukraine
- **WannaCry (2017)** – attributed to North Korea
- **SolarWinds (2020)** – Russian supply-chain attack on US

**Difference:**
- **Cybercrime** = financial motive, individuals
- **Cyber Terrorism** = political motive, civilian terror
- **Cyber Warfare** = state-vs-state conflict

---

### Q11. Distributed Denial of Service (DDoS)
**DDoS Attack** is a malicious attempt to disrupt normal traffic of a server, service, or network by overwhelming it with a **flood of internet traffic from multiple compromised computers (botnets)**.

**How it Works:**
```
Attacker
   ↓ (commands)
[Botnet of 1000s of zombie computers]
   ↓ (flood requests)
Target Server → OVERWHELMED → Service Unavailable
```

**Steps:**
1. Attacker compromises many systems → builds botnet
2. Attacker sends single command to all bots
3. Bots simultaneously flood target with traffic
4. Target's bandwidth/resources exhausted → legitimate users denied service

**Types:**
1. **Volumetric Attacks** – UDP flood, ICMP flood, amplification attacks
2. **Protocol Attacks** – SYN flood, Ping of Death
3. **Application Layer Attacks** – HTTP flood, Slowloris

**Famous Examples:**
- **GitHub (2018)** – 1.35 Tbps Memcached amplification
- **Dyn DNS (2016)** – Mirai botnet attack on DNS provider
- **AWS (2020)** – 2.3 Tbps

**Mitigation:**
- Rate limiting
- Web Application Firewalls (WAF)
- Anti-DDoS services (Cloudflare, AWS Shield, Akamai)
- Black-hole routing
- CDN

---

### Q12. SQL Injection
**SQL Injection (SQLi)** is a code-injection attack where malicious SQL statements are inserted into input fields of a web application to manipulate the underlying database.

**Example:**
- Login query: `SELECT * FROM users WHERE username='$user' AND password='$pass'`
- Attacker enters in username field: `' OR '1'='1' --`
- Resulting query: `SELECT * FROM users WHERE username='' OR '1'='1' --`
- Always TRUE → **bypass login**

**Types:**
1. **In-band SQLi**
   - **Error-based** – relies on database errors
   - **UNION-based** – combines queries
2. **Inferential (Blind) SQLi**
   - **Boolean-based** – true/false responses
   - **Time-based** – uses sleep delays
3. **Out-of-band SQLi** – uses different channel for response (DNS, HTTP)

**Impact:**
- Data theft (credentials, personal info)
- Authentication bypass
- Data destruction
- Database server compromise

**Prevention:**
- ✅ **Parameterized queries / Prepared statements** (most important)
- ✅ Input validation & sanitization
- ✅ Stored procedures
- ✅ Least-privilege database accounts
- ✅ Web Application Firewall (WAF)
- ✅ Escape special characters

**Famous attacks:** Heartland Payment Systems (2008), 7-Eleven, Sony Pictures.

---

## ====== PROBLEM SET II — UNIT 2: Law of Digital Contracts ======

### Q1. CIA Triad with Diagram
**CIA Triad** is the foundational model of information security defining three core security goals.

**Diagram:**
```
              Confidentiality
                   ▲
                  / \
                 /   \
                /     \
               /  CIA  \
              /  TRIAD  \
             /           \
            /_____________\
       Integrity       Availability
```

**1. Confidentiality** – Information accessible only to authorized users
- Threats: eavesdropping, data theft
- Controls: encryption, access control, MFA

**2. Integrity** – Data remains accurate and unmodified
- Threats: tampering, unauthorized changes
- Controls: hashing, digital signatures, version control

**3. Availability** – Information accessible when needed
- Threats: DoS attacks, hardware failure
- Controls: redundancy, backups, DR plans

**Extended (CIA + AAA):** Authentication, Authorization, Accounting/Auditing.

**Exam Tip:** Always draw the triangle. Mention threats + controls for each.

---

### Q2. Comprehensive Cyber Security Policy
A **Cyber Security Policy** is a formal document defining how an organization protects its information assets.

**Key Components:**
1. **Purpose & Scope** – what the policy covers
2. **Asset Management** – classification & inventory
3. **Access Control Policy** – authentication, authorization
4. **Data Protection** – encryption, classification
5. **Network Security** – firewalls, monitoring
6. **Incident Response Plan**
7. **Acceptable Use Policy** (AUP)
8. **Password Policy** – complexity, rotation
9. **Email & Internet Use Policy**
10. **Physical Security**
11. **Disaster Recovery & BCP**
12. **Training & Awareness**
13. **Compliance** – legal & regulatory
14. **Audit & Review** – periodic policy review

**India's National Cyber Security Policy (2013)** – released by Ministry of Electronics & IT (MeitY) — provides framework for protecting Indian cyberspace.

**Exam Tip:** List 10–12 components clearly with brief explanation.

---

### Q3. Cyber Criminals
**Cyber Criminals** are individuals/groups using computers to commit crimes.

**Types:**

| Type | Description |
|------|-------------|
| **White Hat Hackers** | Ethical hackers, hired to find vulnerabilities |
| **Black Hat Hackers** | Malicious, illegal access |
| **Grey Hat Hackers** | Mix of both — may break law without malicious intent |
| **Script Kiddies** | Unskilled, use existing tools/scripts |
| **Crackers** | Break security for malicious purposes |
| **Insiders** | Employees abusing access |
| **Cyber Terrorists** | Politically-motivated attacks |
| **State-sponsored Actors** | Working for governments (APT groups) |
| **Organized Cyber Criminals** | Profit-driven groups, ransomware gangs |
| **Hacktivists** | Ideologically motivated (e.g., Anonymous) |
| **Phishers / Scammers** | Social engineering attackers |
| **Disgruntled employees** | Revenge attacks |

**Motivations:** Financial gain, political/ideological, espionage, fame, revenge, curiosity.

---

### Q4. Attack & Cyber Warfare
**Attack** – Any deliberate attempt to gain unauthorized access, modify, destroy, or steal data, or disrupt services.

**Cyber Warfare** – Politically-motivated cyber attacks **between nation-states** to disrupt critical infrastructure, conduct espionage, or sabotage.

**Cyber Warfare Tools:**
- **Malware:** Stuxnet, NotPetya, WannaCry
- **DDoS attacks** – on military/government sites
- **APT (Advanced Persistent Threats)** – long-term covert attacks
- **Zero-day exploits** – unknown vulnerabilities
- **Supply chain attacks** – SolarWinds

**Notable Cyber Warfare Incidents:**

| Year | Incident | Attribution |
|------|----------|-------------|
| 2007 | Estonia DDoS | Russia (alleged) |
| 2010 | Stuxnet (Iran nuclear) | US-Israel |
| 2015 | Ukraine power grid | Russia |
| 2017 | NotPetya | Russia |
| 2017 | WannaCry | North Korea |
| 2020 | SolarWinds | Russia (SVR/APT29) |

**Indian context:** Mumbai 26/11 attackers used satellite phones; ongoing cyber espionage from China & Pakistan-based groups.

---

### Q5. Indian Cyberspace
**Indian Cyberspace** = the digital ecosystem of India: internet infrastructure, users, applications, platforms, and laws.

**Key Statistics:**
- 800+ million internet users (2nd largest globally)
- 1.4+ billion Aadhaar IDs (largest biometric system)
- UPI processes 10+ billion transactions/month

**Initiatives:**
- **Digital India** (2015) – digitizing services
- **Aadhaar** – unique ID for residents
- **UPI** (Unified Payments Interface)
- **DigiLocker, e-Sign, e-Mudra**

**Cyber Security Bodies:**
- **CERT-In** – Computer Emergency Response Team (under MeitY)
- **NCIIPC** – National Critical Information Infrastructure Protection Centre
- **I4C** – Indian Cyber Crime Coordination Centre (under MHA)
- **CCA** – Controller of Certifying Authorities

**Legal Framework:** IT Act 2000 (amended 2008), DPDP Act 2023.

**Challenges:** Rising cybercrime, Aadhaar leaks, banking fraud, lack of awareness, cross-border crimes.

---

### Q6. Role of International Laws
International cyber laws play crucial role in global cyber governance:

**Key International Laws/Treaties:**

1. **Budapest Convention on Cybercrime (2001)** – first international treaty; covers offences against computer data
2. **Council of Europe Cybercrime Convention** – cooperation between countries
3. **GDPR (EU, 2018)** – General Data Protection Regulation
4. **UNCITRAL Model Law on E-Commerce (1996)** – basis for India's IT Act
5. **CLOUD Act (US, 2018)** – cross-border data access
6. **Wassenaar Arrangement** – export of cyber-surveillance tools

**Roles:**
1. Establish jurisdiction across borders
2. Enable cooperation in cybercrime investigation
3. Standardize legal frameworks globally
4. Address extradition of cybercriminals
5. Protect data across borders
6. Set norms for state behavior in cyberspace

**Limitations:**
- Sovereignty issues (different nations, different laws)
- Enforcement challenges
- Slow ratification
- Conflicts between laws (e.g., GDPR vs CLOUD Act)

---

### Q7. Cyber Forensics
**Cyber Forensics** (Digital Forensics) is the **scientific process** of identifying, preserving, analyzing, and presenting digital evidence in a manner that is **legally admissible in court**.

**Branches:**
1. **Computer Forensics** – hard drives, files, OS artifacts
2. **Network Forensics** – traffic, logs, packet captures
3. **Mobile Device Forensics** – phones, tablets, apps
4. **Cloud Forensics** – cloud-stored data
5. **Database Forensics** – SQL logs, transactions
6. **Email Forensics** – tracing sender, headers, attachments
7. **Memory (RAM) Forensics** – volatile data analysis
8. **IoT Forensics** – smart devices

**Goals:** Identify perpetrator, recover evidence, prove intent, support legal action.

---

### Q8. Need for Computer Forensics
1. **Investigation of cybercrimes** – hacking, fraud
2. **Recovery of deleted/lost data**
3. **Identification of perpetrators**
4. **Legal evidence collection** – admissible in court
5. **Compliance & Audit** – regulatory requirements
6. **Insurance claims** – proof of incident
7. **Internal corporate investigations** – misconduct, fraud
8. **Intellectual property theft cases**
9. **Whistle-blower investigations**
10. **Incident response after a breach**
11. **Civil litigation** – e-discovery
12. **Counter-intelligence**

**Key principle:** Maintain **chain of custody** to ensure evidence is admissible.

---

### Q9. Email Forensics Tools
1. **MailXaminer** – comprehensive email analysis
2. **Aid4Mail** – email migration & forensics
3. **Forensic Email Collector (FEC)** – acquisition
4. **eMailTrackerPro** – trace email origin
5. **EnCase** – general forensic suite (with email module)
6. **Paraben Email Examiner**
7. **MailMiner**
8. **OST Recovery Tool**
9. **Kernel for OST to PST Converter**
10. **FTK (Forensic Toolkit)** – includes email analysis
11. **Autopsy** – open-source forensic platform
12. **Xtraxtor**

**Capabilities:** Header analysis, IP tracing, attachment recovery, deleted email recovery, metadata extraction, keyword search.

---

### Q10. Challenges in Computer Forensics
1. **Encryption** – data hard to access without keys
2. **Anti-forensic techniques** – data wiping, steganography
3. **Volume of data** – TB-scale storage
4. **Cloud storage** – data not on local devices, jurisdiction issues
5. **Mobile device diversity** – varied OS, apps, encryption
6. **Legal jurisdiction** – cross-border data
7. **Volatility of data** – RAM lost on shutdown
8. **Wireless networks** – tracing difficult
9. **Lack of skilled professionals**
10. **Rapidly evolving technology** – AI, IoT, blockchain
11. **Time constraints** – legal deadlines
12. **Privacy laws** vs investigation needs
13. **Authentication of evidence** – proving non-tampering
14. **Cost of tools & training**

---

### Q11. Legal Challenges in Cyber Security
1. **Jurisdiction issues** – cross-border crimes (which country's law applies?)
2. **Inadequate laws** for new technologies (AI, IoT, blockchain, deepfakes)
3. **Anonymous nature of internet** – attackers use VPNs, Tor
4. **Difficulty in evidence preservation** – volatile, easily altered
5. **Privacy vs Security tradeoff** – surveillance laws
6. **Identification of perpetrators** – attribution problem
7. **International cooperation challenges** – different legal systems
8. **Outdated legal frameworks** – laws lag behind tech
9. **Compliance complexity** – multiple regulations (GDPR, DPDP, HIPAA)
10. **Encryption challenges** – privacy vs investigation
11. **Lack of awareness among judges/lawyers** of technical aspects
12. **Data sovereignty** – where data is stored matters

---

### Q12. Analysis Stage in Digital Forensics Lifecycle

**Digital Forensics Lifecycle (6 stages):**

```
1. Identification → 2. Preservation → 3. Collection
       ↓
4. Examination → 5. Analysis → 6. Presentation
```

**Analysis Stage in Detail:**

The analysis phase interprets the data extracted in the examination phase to **answer the questions: who, what, when, where, why, how**.

**Activities in Analysis:**
1. **Reconstruction of events** – timeline of attack
2. **Timeline analysis** – ordering events chronologically
3. **Recovery of deleted/hidden files**
4. **Keyword searches** – find evidence
5. **Metadata analysis** – file dates, owners
6. **Correlation of events** – connecting logs from multiple sources
7. **Identifying tools** used by attacker
8. **Network artifact analysis** – IPs, URLs, payloads
9. **Reaching conclusions** – who did what, when, how
10. **Identifying additional evidence sources**

**Output:** Analysis report with findings ready for presentation in court.

**Key principle:** Analysis must be repeatable and verifiable by another examiner.

---

## ====== PROBLEM SET III — UNIT 3: Information Technology Act 2000 ======

### Q1. Copyright Law and Patent Law

#### Copyright Law
**Definition:** Legal protection given to original creative works (literary, artistic, musical, software code).

**Indian Law:** Copyright Act, 1957 (amended several times).

**Key Points:**
- Protects **expression** of ideas, not ideas themselves
- **Duration:** Author's lifetime + 60 years (literary, artistic)
- Software is protected as a **literary work**
- Rights: Reproduction, Distribution, Adaptation, Public Performance, Communication
- Registration is **not mandatory** but advisable
- Section 63: imprisonment up to 3 years for infringement

**Examples:** Books, songs, paintings, software, films.

---

#### Patent Law
**Definition:** Legal protection for **inventions** that are new, useful, and non-obvious.

**Indian Law:** Patents Act, 1970 (amended).

**Three Criteria (Patentability):**
1. **Novelty** – must be new
2. **Inventive step / Non-obviousness**
3. **Industrial Application / Utility**

**Key Points:**
- **Duration:** 20 years from date of filing
- Categories: Process, Machine, Manufacture, Composition of Matter
- **Software per se NOT patentable** in India (Section 3(k))
- **Hardware-software combination** with technical effect can be patented
- Application filed at Indian Patent Office (Mumbai, Kolkata, Chennai, Delhi)

**Difference Table:**

| Feature | Copyright | Patent |
|---------|-----------|--------|
| Protects | Expression of ideas | Inventions |
| Duration | Lifetime + 60 yrs | 20 years |
| Registration | Not mandatory | Mandatory |
| Examples | Books, software code | Machines, processes |
| Law | Copyright Act 1957 | Patents Act 1970 |

---

### Q2. IT Act 2000 — Sections 43, 45, 65, 68

#### Section 43 – Penalty for damage to computer
Whoever, without permission of the owner, accesses or causes damage to a computer system shall be liable for **compensation up to ₹1 crore** (now unlimited after 2008 amendment).

**Acts covered:**
- Unauthorized access
- Downloading/copying data
- Introducing virus/contaminant
- Damaging data, computer
- Disrupting computer
- Denying access to authorized user
- Charging another person's account
- Stealing/destroying source code

#### Section 45 – Residuary Penalty
Where no specific penalty is provided in the Act, fine **up to ₹25,000** for contravention.

#### Section 65 – Tampering with Computer Source Documents
Whoever knowingly **conceals, destroys, or alters** computer source code (which is required to be maintained by law) faces:
- **Imprisonment up to 3 years** AND/OR
- **Fine up to ₹2 lakh**

**Source Documents** = listing of programs, computer commands, design, layouts.

#### Section 68 – Power of Controller to Give Directions
The **Controller of Certifying Authorities (CCA)** can direct any CA or person to comply with provisions.

**Penalty for non-compliance:**
- Imprisonment up to 2 years AND/OR
- Fine up to ₹1 lakh

---

### Q3. Domain Name and Related Issues
**Domain Name:** Human-readable address that maps to an IP address (e.g., google.com → 142.250.190.46).

**Structure:**
```
www . google . com
 ↑      ↑       ↑
 |      |     TLD (.com, .org, .in)
 |      |
 |   Second-level domain
 |
Subdomain
```

**Common TLDs:**
- gTLDs: .com, .org, .net, .edu, .gov
- ccTLDs: .in, .uk, .us, .jp
- New gTLDs: .app, .blog, .xyz

**Major Issues:**

1. **Cybersquatting** – registering trademark/famous name as domain to sell at high price
   - *Example:* Registering `tata.com` to sell back to Tata Group

2. **Typosquatting** – registering misspellings (`gogle.com`, `facebok.com`) to trick users

3. **Domain Hijacking** – unauthorized transfer of domain ownership

4. **Trademark Conflicts** – same trademark in different countries
   - *Example:* Apple Records vs Apple Computers

5. **Reverse Domain Hijacking** – falsely claiming trademark to take legitimate domain

6. **Phishing Domains** – similar-looking domains (`paypa1.com` vs `paypal.com`)

**Resolution Mechanism:**
- **ICANN's UDRP** (Uniform Domain-Name Dispute Resolution Policy)
- **INDRP** (.IN Domain Name Dispute Resolution Policy) for .in
- WIPO Arbitration

**Famous case:** Yahoo! Inc. vs Akash Arora (1999) — cybersquatting case in India.

---

### Q4. Patents in Cyber World — Process

**Process of Obtaining a Patent:**

```
Step 1: Idea/Invention
        ↓
Step 2: Patent Search (check existing patents)
        ↓
Step 3: Drafting Specification (Provisional or Complete)
        ↓
Step 4: Filing Application at Patent Office
        ↓
Step 5: Publication (18 months after filing)
        ↓
Step 6: Request for Examination (within 48 months)
        ↓
Step 7: Examination by Patent Examiner
        ↓
Step 8: Response to Objections (FER)
        ↓
Step 9: Pre-grant Opposition (if any)
        ↓
Step 10: Grant of Patent (valid for 20 years)
        ↓
Step 11: Renewal Fees (annual)
```

**Patents in Cyber World:**
- **Software per se NOT patentable** in India (Sec 3(k) of Patents Act)
- **What can be patented:** novel hardware-software combination producing **technical effect** (e.g., new algorithm in chip design)
- **Business methods** not patentable in India
- **US allows software patents more liberally** (e.g., Amazon's 1-click)

**Cyber-related Patentable Subject Matter:**
- New encryption algorithms (with hardware)
- Network protocols
- Hardware innovations
- Specific software-hardware combinations
- Telecommunication innovations

**Key Issue:** Distinction between abstract algorithm (not patentable) and applied invention (patentable).

---

### Q5. Why We Use Digital Signature
**Digital Signature** is the mathematical equivalent of a handwritten signature, providing authenticity and integrity to digital documents.

**Reasons / Benefits:**

1. **Authentication** – verifies sender's identity
2. **Integrity** – ensures document not altered after signing
3. **Non-repudiation** – sender cannot deny having signed
4. **Legal Validity** – recognized under IT Act 2000 (Sec 5)
5. **Replaces handwritten signatures** for electronic records
6. **Faster transactions** – no physical paperwork
7. **Cost-effective** – paperless, no courier
8. **Secure** – uses PKI (Public Key Infrastructure)
9. **Time-stamping** – records exact time of signing
10. **Globally accepted** for cross-border transactions

**Mandatory Use Cases in India:**
- GST Returns
- Income Tax Returns (above threshold)
- MCA Filings (company forms)
- e-Tendering
- Trademark/Patent applications
- e-Procurement

**Working (RSA-based):**
1. Hash of document is computed
2. Hash encrypted with **sender's private key** = digital signature
3. Receiver decrypts with **sender's public key** → recovers hash
4. Computes hash of received document
5. If hashes match → document is authentic & unaltered

---

### Q6. Role and Function of Certifying Authorities (CA)

**Certifying Authority (CA)** is a trusted third-party entity authorized to issue **digital signature certificates (DSC)** under Section 18 of IT Act 2000.

**Functions of a CA:**

1. **Issue Digital Signature Certificates (DSC)**
2. **Verify identity** of the subscriber (KYC, Aadhaar, video verification)
3. **Maintain certificate database** (public repository)
4. **Suspend or revoke** certificates when needed
5. **Publish Certificate Revocation List (CRL)** – list of invalidated certs
6. **Maintain audit trails** of all issued certificates
7. **Comply with Controller's directions**
8. **Protect private keys** using HSM (Hardware Security Modules)
9. **Time-stamping services**
10. **Provide trust services** to users

**Role in PKI:**
- Establishes **trust** in digital transactions
- Bridges **identity** to **cryptographic keys**
- Ensures authenticity of public keys

**In India:**
- Regulated by **Controller of Certifying Authorities (CCA)** under IT Act
- Licensed CAs: **eMudhra, Sify, NIC, IDRBT, Capricorn, NSDL**
- Issues **Class 1, 2, 3** DSCs (different verification levels)

**Class of Certificates:**
- **Class 1** – verifies email (low assurance)
- **Class 2** – verifies identity against trusted database (medium)
- **Class 3** – in-person verification (high assurance, used for e-tendering)

---

### Q7. Offences — Breach of Confidentiality and Privacy

**Section 72 of IT Act 2000** – Penalty for breach of confidentiality and privacy.

**Provisions:**
> Any person who, having secured access to electronic records, books, registers, correspondence, information, document or other material under powers conferred by IT Act, **discloses such information without consent** of the person concerned shall be liable.

**Punishment:**
- **Imprisonment up to 2 years**, OR
- **Fine up to ₹1 lakh**, OR both

**Section 72A** (Added in 2008 amendment) – Punishment for disclosure in breach of lawful contract:
- Imprisonment up to 3 years
- Fine up to ₹5 lakh
- Or both

**Examples of Offences:**
1. Aadhaar enrolment agent leaking applicants' data
2. Bank employee selling customer details
3. Hospital staff sharing patient records
4. Telecom employee selling call records
5. Government official disclosing official documents

**Related Sections:**
- **Section 66E** – Violation of privacy through obscene images (capturing/transmitting private images)
- **Section 67** – Publishing obscene material

**Famous case:** *State of Tamil Nadu vs Suhas Katti* — first conviction under IT Act for posting obscene messages about a divorced woman.

---

### Q8. Regulation of Publication of Information

**Under IT Act 2000, multiple sections regulate online publication:**

#### Section 66A (Struck down by Supreme Court in *Shreya Singhal vs Union of India*, 2015)
Originally prohibited "offensive messages" — declared **unconstitutional** for being vague.

#### Section 67 – Publishing/Transmitting Obscene Material in Electronic Form
- **Punishment:** First conviction — imprisonment up to **3 years** and fine up to **₹5 lakh**
- **Subsequent:** up to **5 years** and fine up to **₹10 lakh**

#### Section 67A – Publishing Sexually Explicit Material
- **Punishment:** Imprisonment up to **5 years** and fine up to **₹10 lakh**

#### Section 67B – Child Pornography
- **Punishment:** Imprisonment up to **5 years** and fine up to **₹10 lakh** (first conviction); harsher for repeat

#### Section 69 – Power to Issue Directions for Interception/Monitoring/Decryption
- Government can intercept, monitor, decrypt info for sovereignty, security, public order

#### Section 69A – Blocking Public Access to Information
- Government can block websites for security/sovereignty reasons
- Used to block ~250 Chinese apps in 2020

#### Section 70 – Protected Systems
- Critical infrastructure can be declared "protected systems"
- Unauthorized access: imprisonment up to 10 years

**Other Regulations:**
- **IT (Intermediary Guidelines and Digital Media Ethics Code) Rules 2021** – social media compliance
- **Cable Television Networks Regulation Act**
- **Press Council of India** – print media ethics
- **Cinematograph Act 1952** – films

---

### Q9. Residual Risk vs Risk Appetite

**Residual Risk:** The risk that **remains AFTER** security controls are implemented.
> Formula: **Residual Risk = Inherent Risk – Risk mitigated by controls**

**Risk Appetite:** The amount of risk an organization is **WILLING TO ACCEPT** in pursuit of its objectives.
- Defined by management
- Aligned with business goals
- Strategic-level decision

**Key Principle:** Residual Risk should be ≤ Risk Appetite. If not, more controls are needed.

**Difference Table:**

| Feature | Residual Risk | Risk Appetite |
|---------|---------------|---------------|
| **Definition** | Risk left after controls | Risk willing to take |
| **Nature** | Calculated/measured | Defined/decided |
| **Source** | Result of controls | Strategic decision |
| **Direction** | Bottom-up | Top-down |
| **Should be** | ≤ Risk Appetite | Sets boundary |
| **Example** | After firewall, residual risk = 5% chance of breach | Org accepts 10% chance of breach |

**Example Scenario:**
- Inherent risk of data breach: 80%
- After implementing controls (firewall, MFA, encryption): risk reduces to 5%
- Residual risk = 5%
- If risk appetite is 10%, then 5% is acceptable. If risk appetite is 2%, more controls needed.

---

### Q10. Authentication vs Authorization

**Authentication:** Verifying **WHO** the user is — confirms identity.
**Authorization:** Verifying **WHAT** the user can access/do — defines permissions.

**Difference Table:**

| Feature | Authentication | Authorization |
|---------|----------------|---------------|
| **Purpose** | Identifies user | Determines access level |
| **Order** | Comes FIRST | Comes AFTER authentication |
| **Question** | "Are you who you claim to be?" | "What are you allowed to do?" |
| **Methods** | Password, biometric, OTP, smart card | Roles, permissions, ACLs |
| **Output** | Yes/No (allowed in or not) | List of allowed resources |
| **User-visible** | Yes (login screen) | No (transparent) |
| **Example** | Login with username + password | Admin can delete; user can only view |

**Real-life Example — Gmail Login:**

1. **Authentication:** You enter `apsingh@bluematter.com` + password → Gmail verifies it's really you.
2. **Authorization:** Once logged in, you can:
   - ✅ Read **YOUR** emails
   - ❌ Cannot read someone else's emails
   - ✅ Send emails from your account
   - ❌ Cannot delete others' emails

**3-Factor Authentication:**
1. Something you **know** (password)
2. Something you **have** (phone, OTP)
3. Something you **are** (fingerprint)

**Authorization Models:**
- **DAC** (Discretionary Access Control)
- **MAC** (Mandatory Access Control)
- **RBAC** (Role-Based Access Control)
- **ABAC** (Attribute-Based Access Control)

---

### Q11. Intellectual Property Crime

**Intellectual Property (IP) Crime** = unauthorized use, copying, or distribution of someone's legally protected creations of the mind.

**Types of IP Crimes:**

1. **Copyright Infringement** – illegal copying of software, music, movies, books
2. **Trademark Infringement** – unauthorized use of brand names/logos
3. **Patent Infringement** – using patented invention without permission
4. **Trade Secret Theft** – stealing confidential business info
5. **Counterfeiting** – fake products (medicines, electronics)
6. **Piracy** – unauthorized reproduction (software piracy, movie piracy)
7. **Industrial Design Infringement**
8. **Geographical Indication (GI) Misuse** – e.g., fake Darjeeling tea

**IP Crimes in Cyber World:**
1. **Online piracy** – torrents, streaming sites
2. **Software cracking** – removing license checks
3. **Domain name squatting**
4. **Deep linking** – linking inside another site bypassing homepage
5. **Illegal downloads** of music, books, movies
6. **Click fraud** – fake clicks on online ads
7. **Brand abuse** – fake e-commerce sites
8. **Jailbreaking/Rooting** – may infringe DRM

**Legal Provisions:**

| Crime | Indian Law | Punishment |
|-------|-----------|------------|
| Copyright Infringement | Sec 63, Copyright Act | Up to 3 yrs + fine |
| Trademark Infringement | Trade Marks Act 1999 | Up to 3 yrs + fine |
| Patent Infringement | Patents Act 1970 | Civil + injunction |
| Trade Secret | Common law / contracts | Damages |

**IT Act sections** also apply for cyber-related IP crimes (Sec 43, 65, 66).

---

### Q12. IT Act 2000 — Sections 46–64 and CRAT Rules

#### Section 46–47 – Adjudicating Officer
- **State Government** appoints Adjudicating Officer (must be at Joint Secretary level)
- Powers: Adjudicate cases where compensation/penalty up to **₹5 crore**
- Has powers of a **civil court** (summon witnesses, examine evidence)
- Appeals against AO decision go to Cyber Appellate Tribunal

#### Section 48–56 – Cyber Appellate Tribunal (CRAT)
*(Now merged with TDSAT — Telecom Disputes Settlement and Appellate Tribunal, since 2017)*

- Established under Section 48
- **Composition:** Chairperson + members appointed by Central Govt
- **Qualifications:** Chairperson — qualified to be HC judge; members — sufficient expertise
- **Powers:** Like a civil court — summon, examine, accept evidence
- Bound by **principles of natural justice**, not strict CPC rules

#### Section 57 – Appeal from CRAT to High Court
- Within **60 days** from order
- On any question of fact or law

#### Section 58 – Procedure & Powers of CRAT
- Powers of civil court under CPC for:
  - Summoning witnesses
  - Discovery & inspection
  - Receiving evidence on affidavit
  - Reviewing decisions
  - Dismissing applications

#### Section 59 – Right to Legal Representation
- Parties may appear personally OR through legal practitioner

#### Section 60 – Limitation
- Limitation Act 1963 applies

#### Section 61 – Civil Court Jurisdiction Barred
- No civil court has jurisdiction to entertain matters covered under IT Act

#### Section 62 – Appeal to High Court
- (Section 57 details)

#### Section 63 – Compounding of Contraventions
- Adjudicating Officer can compound contraventions before judgment

#### Section 64 – Recovery of Penalty
- Penalty unpaid → recovered as land revenue arrears

---

#### CRAT Rules (Cyber Regulations Appellate Tribunal Rules)
The CRAT Rules detail procedural aspects:

1. **Filing of appeal** – within 45 days of AO order, with prescribed fee
2. **Forms** – Form A (memorandum of appeal), Form B (interlocutory)
3. **Service of notice** – on respondents
4. **Hearing procedure** – as per natural justice
5. **Costs** – tribunal can award costs
6. **Ex-parte orders** – if respondent absent
7. **Modification, review** of orders
8. **Records management**
9. **Appellate procedure** to High Court

**Note:** CRAT was dissolved in 2017; appeals now go to **TDSAT**.

---

# END OF PROBLEM SET SOLUTIONS

> **Total: 36 questions** (12 from each Unit I to III)
> Note: No problem sets provided for Units IV and V; refer to syllabus notes for those topics.
