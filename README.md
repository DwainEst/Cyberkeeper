# 🛡️ Cyberkeeper — Computer Science and Penetration Testing Resource

> A public portfolio of work in penetration testing & Computer Science. Includes write-ups, tooling notes and other useful Computer Science related information by **Dwain Esterhuizen**.  

<a href="https://www.linkedin.com/in/dwain-est" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-0072b1?&style=for-the-badge&logo=linkedin&logoColor=white" /></a> 

[![GitHub followers](https://img.shields.io/github/followers/DwainEst?label=Follow&style=social)](https://github.com/DwainEst) ![License](https://img.shields.io/github/license/DwainEst/Cyberkeeper)

---

## 📑 Table of Contents
1. [About This Repo](#about-this-repo)
2. [How I Work — Rules of Engagement & Methodology](#how-i-work--rules-of-engagement--methodology)
3. [Projects / Write-ups](#projects--write-ups)
4. [Tools & Skills](#tools--skills)
5. [How to Run Lab Artifacts Locally](#how-to-run-lab-artifacts-locally)
6. [Report & Artifact Structure](#report--artifact-structure)
7. [Responsible Disclosure & Ethics](#responsible-disclosure--ethics)
8. [Contributing / Forks](#contributing--forks)
9. [License & Contact](#license--contact)

---

## 🧩 About This Repo

This repository is my **public collection of work in penetration testing and security research**.  
It includes:
- Detailed engagement write-ups (redacted for safety and confidentiality)
- Recreated vulnerable lab examples for learning and demonstration
- Scripts, notes, and playbooks I use during engagements
- Templates for reports and proof-of-concept (PoC) artifacts

> ⚠️ **Note:** All real engagements are redacted to protect client confidentiality. When permitted, I include sanitised screenshots and sample payloads that are safe for public sharing.

---

## ⚙️ How I Work — Rules of Engagement & Methodology

Although every client and the subsequent engagment is unique. I follow a general but clear, repeatable process throughout every client engagement:

1. **Pre-engagement & Scoping**  
   - Quotation, Service agreement and Confirmation of engagement.
   - Confirm rules of engagement (ROE), targets, scope, exclusions, and legal authorisation.
2. **Testing**
  2.1. **Reconnaissance**  
       - Passive and active information gathering (OSINT, Asset discovery).
  2.2. **Discovery: Vulnerability Identification**  
       - Scanning, fuzzing, and manual exploration.
  2.3. **Exploitation / PoC**  
       - Controlled exploitation, safe PoC creation, no persistence unless authorized.
  2.4. **Post-exploitation & Impact Analysis**  
       - Data exposure analysis, lateral movement (if in scope).
  2.5. **Report Writing**
       - Capturing steps taken along with actionable remediation guidance.
3. **Reporting**  
   - Presenting the actionable remediation guidance with prioritised findings.
4. **Retest (if required/agreed)**

All work adheres to ethical hacking principles and responsible disclosure standards.

---

## 💼 Projects / Write-ups

Each project folder contains a structured write-up, PoCs, and sanitized evidence.

### Example: `projects/2025-07-internal-webapp/`

**Title:** Internal Web App — Auth Bypass → RCE (sanitized)  
**Scope:** Internal IP range — assets A, B (redacted)  
**Summary:** Authentication bypass through predictable session tokens → remote code execution via insecure deserialization.  
**Highlights:**
- CVSS: 9.1 (High)
- Safe PoC for access-level verification (sanitized)

**Files:**
- `writeup.md` — full, redacted report  
- `pocs/` — sanitized proof-of-concept scripts  
- `screenshots/` — redacted evidence  

**Path:** [`projects/2025-07-internal-webapp/writeup.md`](projects/2025-07-internal-webapp/writeup.md)

---

## 🧾 Project / Write-up Template

Use this template for each new engagement.

```markdown
# Project Title — YYYY-MM

## Overview
- Client (redacted): Example Corp
- Scope: [list of targets]
- Date: YYYY-MM-DD

## Summary & Impact
- Executive summary for non-technical stakeholders.
- Impact rating (High / Medium / Low).

## Findings (ordered by risk)
### Finding 1 — Title
- CVSS (if applicable)
- Description
- Reproduction steps (non-destructive)
- Evidence (redacted)
- Remediation

### Finding 2 — Title
...

## PoC & Artifacts
- `poc.sh` (sanitized)
- `screenshots/`

## Lessons Learned & Follow-up Actions


