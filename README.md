# SOC Incident Investigation – RDP Brute Force With Successful Authentication

## 📌 Overview
This repository documents a hands-on **Security Operations Center (SOC)** investigation of an **RDP brute-force attack that resulted in a successful authentication** against a Windows endpoint.  
The investigation focuses on evidence-based analysis, timeline reconstruction, MITRE ATT&CK mapping, and impact assessment using standard SOC methodologies.

---

## Incident Summary
- **Incident Type:** RDP Brute Force with Successful Authentication  
- **Detection Source:** Security Logs / RDP Authentication Events  
- **Severity:** Medium  
- **Date Observed:** 2026-01-15  
- **Status:** No Post-Compromise Activity Observed  

---

## Affected Assets
- **Host / Device Name:** MTS-ContractorPC2  
- **IP Address:** 192.168.10.10  
- **Operating System:** Windows  
- **User Account(s):** Windows user account (name redacted)  

---

## Threat Actor Details
- **Source IP Address:** 14.136.73.18  
- **Geolocation:** External network infrastructure  
- **Reputation / OSINT Summary:**  
  The IP address has been associated with prior brute-force-related activity. While no high-confidence malicious reputation was confirmed, the observed behavior aligns with credential-access reconnaissance patterns.

---

## Investigation Timeline (UTC)

| Time (UTC) | Event |
|------------|-------|
| 2026-01-15 19:41:10 | External IP 14.136.73.18 established inbound RDP connection to 192.168.10.10 |
| 2026-01-15 19:46:35 | Successful RDP authentication recorded |
| Post-authentication | No suspicious processes, persistence, or lateral movement observed |

---

## Investigation Details
An external IP address conducted **41 RDP brute-force attempts** against a Windows workstation.  
Between **19:41:10 and 19:46:35 UTC**, the attacker successfully authenticated via RDP.

Post-authentication telemetry was reviewed to validate potential compromise activity. Analysis confirmed:
- No suspicious process execution  
- No file or registry modifications  
- No persistence mechanisms  
- No lateral movement to other internal systems  

The investigation validated that the successful authentication did **not** result in observable malicious activity.

---

## Tools & Techniques Used
- **SIEM / Platform:** Log analysis / Security event review  
- **Log Sources:** RDP authentication and connection logs  
- **Query Language:** Native log queries  

---

## MITRE ATT&CK Mapping

| Technique ID | Technique Name |
|-------------|----------------|
| T1110 | Brute Force |
| T1078 | Valid Accounts |

---

## Impact Assessment
- Successful authentication: **Yes**  
- Evidence of persistence: **No**  
- Lateral movement observed: **No**  
- Data exfiltration detected: **No**  

**Assessment Summary:**  
Although the attacker successfully authenticated via RDP, no evidence of post-compromise activity was identified.  
The overall impact is assessed as **limited**, however the event represents a **confirmed security control failure** and increased risk exposure.

---

## Recommendations
- Reset credentials for the affected user account  
- Enforce **multi-factor authentication (MFA)** for RDP access  
- Restrict RDP exposure using VPN or IP allow-listing  
- Enable account lockout policies to prevent brute-force attempts  
- Continue monitoring for delayed or follow-on activity from the source IP  

---

## Evidence & Artifacts
- RDP authentication logs  
- Network connection records  
- Timeline correlation notes

---

## Key Takeaways
- Successful authentication does not always equate to confirmed compromise  
- Post-authentication validation is critical for accurate impact assessment  
- RDP exposure without MFA significantly increases attack surface  

---

## 🚀 About This Portfolio
This repository is part of my **SOC analyst portfolio**, showcasing hands-on incident investigations, structured analysis, and alignment with real-world SOC workflows.

> ⚠️ All data used in this report is simulated or anonymized for educational purposes only.
