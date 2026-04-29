<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=26&pause=1000&color=2E6DA4&center=true&vCenter=true&width=800&lines=%23AppSecFromTheTrenches;Enterprise+Field+Notes+%7C+6%2B+Years+of+Real+Engagements;Web+%7C+API+%7C+Red+Team+%7C+Threat+Intelligence;200%2B+Critical+%26+High+Findings+Documented" alt="Typing SVG" />

> **Not a learning series. A practitioner's field manual.**
> *Every write-up is a pattern I have confirmed in production enterprise environments.*

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Dheeraj%20Kumar%20Jayaswal-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/dheerajkumarjayaswal)
[![GitHub](https://img.shields.io/badge/GitHub-dheeraj--jayaswal-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/dheeraj-jayaswal)
[![Role](https://img.shields.io/badge/Role-Technology%20Lead%20%E2%80%93%20Offensive%20Security-FF6B35?style=for-the-badge)](https://linkedin.com/in/dheerajkumarjayaswal)
[![Org](https://img.shields.io/badge/Infosys%20Limited-Pune%2C%20India-0078D6?style=for-the-badge)](https://linkedin.com/in/dheerajkumarjayaswal)

</div>

---

## 📌 What Is This Repository?

This is the official GitHub home of **AppSec From The Trenches** — an enterprise application security reference documenting real vulnerability patterns, exploitation chains, and professional testing methodology built from **6+ years of penetration testing at Infosys Limited** across BFSI, Healthcare, Retail, E-commerce, Freight Logistics, and Education sectors.

### How this differs from typical security write-ups

| Standard Tutorial | AppSec From The Trenches |
|---|---|
| Generic code examples | C# ASP.NET / Java Spring — the actual stacks I test |
| `alert(1)` as the goal | Full exploitation chain to account takeover |
| Beginner walkthrough | Professional pentest report format with CVSS scoring |
| Single technique | Chained findings showing real business impact |
| "Try this on DVWA" | "I found this on a real enterprise system" |

Every write-up answers **5 professional questions:**
1. What is this vulnerability? *(root cause, not just definition)*
2. Why does it consistently appear in enterprise apps? *(developer patterns and deadline pressures)*
3. How do I find it efficiently? *(Burp Suite workflow, not just payload lists)*
4. How do I demonstrate real business impact? *(beyond `alert(1)`)*
5. What goes in the client report? *(CVSS, PoC, remediation, secure code)*

---

## 🧠 The Developer-to-Attacker Advantage

I started as a full-stack developer — ASP.NET, SQL Server, JavaScript. Six years of application security testing later, that background remains my biggest edge.

```
What most testers ask: "Is this input field vulnerable?"
What I ask:           "Why did the developer build it this way,
                       and where does that pattern break?"

The developer assumption that breaks enterprise APIs:
  "Only our frontend calls these endpoints"
  → Wrong. Any HTTP client with a valid token can call them.

The developer assumption that creates BOLA:
  "[Authorize] attribute validates the token = the endpoint is secure"
  → Wrong. Authentication ≠ authorisation.
  → The ownership check is a separate, explicit requirement.
  → Under deadline pressure, developers consistently miss it.

The developer pattern that creates mass assignment:
  @RequestBody User user → framework binds ALL JSON fields
  → Including role, isAdmin, subscriptionPlan
  → Developer never expected users to send those fields
  → They do.
```

Understanding why code is written a certain way tells you exactly where to look for the gap.

---

## 🗂️ Categories Covered

<table>
<tr>
<td valign="top" width="50%">

### 🔍 Reconnaissance & OSINT
Subdomain enumeration, certificate transparency, GitHub secret scanning, Shodan/Censys asset mapping, JavaScript bundle analysis, source map exposure, Wayback Machine endpoint recovery, passive DNS intelligence, technology fingerprinting.

### 🔑 Authentication & Session Security
Brute force and credential stuffing, OTP/MFA bypass (response manipulation, direct endpoint access, OTP brute force), session fixation, cookie security attributes, JWT attacks — alg:none, weak HS256 secrets (hashcat), RS256→HS256 algorithm confusion, kid parameter injection, OAuth state bypass, SAML vulnerabilities, SSO misconfiguration, token replay after logout.

### 🛡️ Access Control — BOLA, BFLA, IDOR
BOLA across all HTTP methods (GET/PUT/DELETE/PATCH), vertical IDOR/privilege escalation, mass assignment at registration and update endpoints, CSRF across all variants and bypass techniques, forced browsing, HTTP method override, 403 bypass techniques, second-order IDOR, file download IDOR chains.

### 💉 Injection Vulnerabilities
SQL injection — error-based, union, blind boolean, time-based, second-order, out-of-band; NoSQL injection in MongoDB APIs; ORM injection; OS command injection; SSTI across Jinja2, Twig, Freemarker, Velocity, OGNL; LDAP injection; log injection; CSV injection; template literal injection.

### 🕸️ XSS & Client-Side Attacks
Reflected, stored, DOM-based, blind XSS with Burp Collaborator; mXSS; XSS in API responses rendered by React/Angular; dangerouslySetInnerHTML exploitation; CSP bypass — JSONP, unsafe-inline, nonce prediction; XSS → session theft → ATO full chain documentation.

### 🌐 SSRF & XXE
Basic and blind SSRF, SSRF to AWS/GCP/Azure cloud metadata credential theft, IMDSv1 vs IMDSv2, SSRF filter bypasses — decimal encoding, IPv6, DNS rebinding, Gopher protocol; XXE in-band and out-of-band, XXE via file upload, billion laughs DoS.

</td>
<td valign="top" width="50%">

### 📁 File Security & Path Traversal
Unrestricted file upload — extension bypass, content-type bypass, magic bytes bypass, null byte injection; path traversal — `/proc/self/environ` as primary target over `/etc/passwd`; LFI including log poisoning → RCE chain; RFI; ZIP slip; source map exposure → credential extraction.

### 💼 Business Logic & Race Conditions
Price manipulation, workflow bypass, coupon stacking, race conditions — Turbo Intruder methodology, double spend, OTP reuse; payment manipulation; refund abuse; quantity manipulation in APIs; negative number exploitation.

### 🔌 API Security — OWASP API Top 10
BOLA, Broken Authentication, Mass Assignment, Rate Limiting Absence, BFLA, Unsafe Business Flows, SSRF via API mutations, Security Misconfiguration, Improper Inventory Management (API versioning), Unsafe API Consumption; GraphQL — introspection, batching bypass, nested BOLA; WebSocket security; gRPC/Protobuf; Swagger/OpenAPI abuse.

### ☁️ Cloud & Infrastructure Security
AWS — S3 misconfiguration, IAM privilege escalation, Lambda security, SSRF → IMDSv1 credential theft, CloudTrail gaps; Azure IMDS; GCP service account token exposure; Kubernetes API unauthenticated access; Docker API exposure (port 2375); CI/CD pipeline security — GitHub Actions, Jenkins; Terraform state exposure; Spring Boot Actuator exploitation.

### 🔐 Cryptography & Secrets
Weak hashing — MD5/SHA-1 without salt; password cracking — hashcat modes and wordlist strategy; JWT cryptographic failures; hardcoded secrets in JavaScript bundles; `.env` and `web.config` credential exposure; API keys in source maps; AWS keys in mobile apps.

### 🔴 Red Team Techniques
Initial access via web application exploitation (T1190), credential stuffing from breach intelligence (T1078), phishing simulation methodology; post-exploitation in authorised engagements; Cobalt Strike/Sliver C2 context; MITRE ATT&CK TTP mapping for all findings; detection gap analysis per finding.

### 🕵️ Threat Intelligence & Dark Web
Pre-engagement credential monitoring (HIBP API), paste site monitoring, ransomware group victim checking (RansomWatch), threat actor profiling (Diamond Model, ATT&CK Groups), brand protection and typosquatting detection (dnstwist), email authentication assessment (SPF/DKIM/DMARC), OSINT-to-TI pipeline automation with Python.

### 🤖 AI / LLM Security
Prompt injection — direct and indirect; insecure plugin execution; LLM agent manipulation; system prompt extraction techniques; RAG poisoning; LLM-integrated application security review.

</td>
</tr>
</table>

---

## 📊 Portfolio Statistics

<div align="center">

| Metric | Value |
|---|---|
| 🏢 Enterprise Engagements | **20+** |
| 🐛 Critical & High Findings Documented | **200+** |
| 📝 Write-ups Published | **Growing** |
| 💼 Years in Enterprise AppSec | **6+** |
| 🏭 Industry Sectors Covered | **6 (BFSI, Healthcare, Retail, E-commerce, Logistics, Education)** |
| 👥 Engineers Mentored on Secure Coding | **15+** |
| 📉 Attack Surface Reduction Achieved | **35%** |

</div>

---

## 🔥 Finding Severity Distribution (Real Engagements)

```
CRITICAL  ████████████████░░░░░░░░░░░░░░  ~25%  BOLA, SQLi RCE, JWT bypass, SSRF metadata
HIGH      ██████████████████████████░░░░  ~45%  Auth bypass, mass assignment, SSRF, XSS-ATO
MEDIUM    █████████████░░░░░░░░░░░░░░░░░  ~23%  Rate limiting, CORS, sensitive data exposure
LOW/INFO  ███░░░░░░░░░░░░░░░░░░░░░░░░░░░  ~7%   Version disclosure, missing headers
```

---

## 📖 How to Use This Repository

### For Security Professionals (Primary Audience)
Each write-up is structured as a professional reference, not a tutorial. It documents the attack pattern, the Burp Suite workflow, the evidence collection standard, and the exact report template — ready for your next enterprise engagement.

### For Bug Bounty Hunters
Every write-up ends with:
- ✅ CVSS v3.1 score with full vector string
- ✅ Reproducible cURL/Burp steps
- ✅ Business impact statement in executive language
- ✅ Complete enterprise report template
- ✅ Secure code fix in C#/ASP.NET or Java (the stacks I test most)

### For Penetration Testers
Write-ups are structured as **professional testing checklists**. Each vulnerability includes:
- Burp Suite workflow (not just tool commands)
- Evidence collection standards (3-screenshot rule)
- ATT&CK technique mapping per finding
- Rate limiting and scope considerations for enterprise environments

### For Security Researchers
The enterprise context distinguishes these notes from CTF walkthroughs. Everything here is grounded in: why this pattern exists in production code, how frequently I find it across real applications, and what the actual business risk is beyond the CVSS number.

---

## 🛠️ Tools Used in This Series

```
Reconnaissance:    subfinder, amass, httpx, ffuf, dnstwist, theHarvester
Intelligence:      Shodan, Censys, HIBP API, SpiderFoot, truffleHog, gitleaks
Web Testing:       Burp Suite Pro (primary), OWASP ZAP (CI/CD), curl, Nikto
API Testing:       Postman, Burp Suite Pro, ffuf, grpcurl
Scanning:          Nmap, Nessus, Nuclei
Network:           Wireshark, Netcat, tshark
Credential:        Hydra, Hashcat, John the Ripper
Exploitation:      Metasploit (auxiliary/confirmation only), sqlmap, ysoserial
                   jwt_tool, jwt.io, Burp JWT Editor extension
Red Team:          Cobalt Strike, Sliver C2, Mimikatz, BloodHound (AD scope)
Dark Web TI:       Tor Browser, OnionSearch, Ahmia, RansomWatch, MISP
Automation:        Python (requests, scapy, pyjwt, paramiko, aiohttp)
DevSecOps:         SonarQube, OWASP ZAP in CI/CD (Newman + Postman)
```

---

## 📂 Repository Structure

```
AppSec-From-The-Trenches/
│
├── README.md
│
├── web-application/               → OWASP Top 10 + enterprise web vulns
│   ├── SQL_Injection_Enterprise_Pentest.md
│   ├── Broken_Authentication_Enterprise_Pentest.md
│   ├── Sensitive_Data_Exposure_Enterprise_Pentest.md
│   ├── XSS_Enterprise_Pentest.md
│   ├── CSRF_Enterprise_Pentest.md
│   ├── IDOR_Enterprise_Pentest.md
│   ├── Security_Misconfiguration_Enterprise_Pentest.md
│   ├── Insecure_Deserialization_Enterprise_Pentest.md
│   ├── SSRF_Enterprise_Pentest.md
│   ├── Path_Traversal_Enterprise_Pentest.md
│   ├── Security_Headers_Enterprise_Pentest.md
│   ├── Cookie_Security_Enterprise_Pentest.md
│   └── JWT_Attacks_Enterprise_Pentest.md
│
├── api-security/                  → OWASP API Top 10 complete coverage
│   ├── README.md                  → API series landing page
│   ├── API_REST_Security_Enterprise.md
│   ├── API_Auth_Methods_Enterprise.md
│   ├── API_GraphQL_Enterprise.md
│   ├── API_Recon_Enterprise.md
│   ├── API_Postman_Enterprise.md
│   ├── API_Swagger_OpenAPI_Enterprise.md
│   ├── API_Versioning_Security_Enterprise.md
│   ├── API_BOLA_Enterprise.md
│   ├── API_Broken_Auth_Enterprise.md
│   ├── API_Mass_Assignment_Enterprise.md
│   ├── API_Rate_Limiting_Enterprise.md
│   ├── API_BFLA_Enterprise.md
│   ├── API_SSRF_Enterprise.md
│   ├── API7_to_10_Enterprise.md
│   └── API_Burp_Suite_Enterprise.md
│
├── tools/                         → Enterprise tool usage guides
│   ├── Burp_Suite_Enterprise_Usage.md
│   ├── OWASP_ZAP_Enterprise_Usage.md
│   ├── Nmap_Enterprise_Usage.md
│   ├── Wireshark_Enterprise_Usage.md
│   ├── Metasploit_Enterprise_Usage.md
│   ├── Netcat_Enterprise_Usage.md
│   ├── Hydra_Enterprise_Usage.md
│   ├── Hashcat_Enterprise_Usage.md
│   ├── JohnTheRipper_Enterprise_Usage.md
│   ├── Nuclei_Enterprise_Usage.md
│   ├── Nessus_Enterprise_Usage.md
│   ├── Curl_Enterprise_Usage.md
│   ├── FFUF_Enterprise_Usage.md
│   ├── SQLMap_Enterprise_Usage.md
│   └── Nikto_Enterprise_Usage.md
│
├── recon-methodology/             → Structured recon workflow
│   ├── OSINT_Recon_Enterprise.md
│   └── Enterprise_Recon_Workflow.md
│
└── pentest-methodology/           → Full engagement framework
    └── Pentest_Methodology_Enterprise.md
```

---

## 🔑 Signature Findings — Patterns I Find Consistently

These are the vulnerability classes I document across nearly every enterprise engagement:

```
1. BOLA on PUT and DELETE (not just GET)
   → Developers protect GET for IDOR. They forget PUT modifies
     and DELETE removes. One IDOR finding becomes three Critical findings.
   → Account takeover chain: BOLA write → email change → password reset

2. JWT HS256 weak secrets
   → Early Spring Boot tutorials used "secret" as the example key.
   → Production apps were deployed from those tutorials.
   → hashcat -m 16500 jwt.txt rockyou.txt → cracks in seconds.
   → Once cracked: forge any identity, any role.

3. Spring Boot Actuator exposed
   → /actuator/env returns database passwords, AWS keys, JWT secrets.
   → Found on ~40% of Java enterprise applications I assess.
   → One endpoint, zero authentication required, Critical finding.

4. Mass assignment at registration
   → Teams harden profile update endpoints after a pentest.
   → They never go back and fix registration.
   → POST /register {"role":"admin"} → accepted more often than it should.

5. Old API versions missing auth checks
   → /api/v2/users/1042 → 403 Forbidden (ownership enforced).
   → /api/v1/users/1042 → 200 OK + victim's full data.
   → "Deprecated" in the roadmap does not mean "disabled" in production.

6. GraphQL introspection in production
   → One query hands the complete data model to any attacker.
   → Type names like "AdminConfig" and "EmployeePayroll" are the roadmap.
   → Found on the majority of GraphQL applications I assess.
```

---

## 🏅 Certifications & Background

| Certification | Status |
|---|---|
| OSCP — Offensive Security | 🔄 In Progress (2025-2026) |
| Certified Ethical Hacker (CEH) | ✅ EC-Council, 2021 |
| AWS Certified Solutions Architect – Associate | ✅ Amazon, 2022 |
| AWS Certified Cloud Practitioner | ✅ Amazon, 2022 |
| Executive Certificate in Cyber Security | ✅ IIT Kanpur, 2026 |

**Professional Background:**
- 15+ years in IT | 6+ years in offensive security
- Started as full-stack developer (ASP.NET / SQL Server / JavaScript)
- Technology Lead — Offensive Security at Infosys Limited, Pune
- Domains: BFSI, Healthcare, Retail, E-commerce, Freight Logistics, Education

---

## ⭐ If This Helped You

If any write-up here helped you find a bug, understand a technique, or sharpen a report — star this repository. It helps other security professionals find this content.

And if you have questions about enterprise security methodology, responsible disclosure, or penetration testing workflows — reach out on LinkedIn.

---

## 👤 About the Author

<div align="center">

**Dheeraj Kumar Jayaswal**
*Technology Lead – Offensive Security | Senior Penetration Tester | Security Researcher*

Enterprise penetration testing, red team operations, and threat intelligence across 20+ applications.
Tested 6 industry verticals. Discovered 200+ Critical and High severity vulnerabilities.

| Platform | Link |
|---|---|
| 🔗 LinkedIn | [linkedin.com/in/dheerajkumarjayaswal](https://linkedin.com/in/dheerajkumarjayaswal) |
| 🐙 GitHub | [github.com/dheeraj-jayaswal](https://github.com/dheeraj-jayaswal) |
| 📧 Email | jaiswal.dheeraj123@gmail.com |
| 🏢 Organisation | Infosys Limited, Pune, India |

</div>

---

## 📜 License & Usage

All content in this repository is published for **educational and professional reference purposes** under the MIT License. All vulnerability techniques described are documented for **defensive security, professional penetration testing, and educational understanding only**.

Every technique in this repository is tested in authorised environments or documented from authorised professional engagements. Unauthorised testing of systems you do not own or have explicit permission to test is illegal in most jurisdictions.

---

<div align="center">

*"The best penetration testers think like developers first and attackers second.*
*If you understand why code was built a certain way, you will always find more than any scanner ever will."*

**#AppSecFromTheTrenches · #PenTest · #BugBounty · #WebSecurity · #APISecuity · #EnterpriseSecurity**

</div>
