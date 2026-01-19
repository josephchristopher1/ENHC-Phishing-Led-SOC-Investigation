# England National Health Centre (ENHC)
## Phishing-Led Endpoint & Credential Compromise Simulation

**Organisation:** England National Health Centre (ENHC)  
**Sector:** Healthcare / Public Health Services  
**Cybersecurity Function:** Blue Team (SOC)  
**Lead Analyst:** Joseph Christopher  
**Date:** January 2026  

---

## Executive Summary

This project documents a phishing-led security incident simulation conducted within the England National Health Centre (ENHC) internal environment. The exercise demonstrates a full end-to-end SOC investigation workflow, from initial phishing delivery to detection, containment, and post-incident review.

The investigation was evidence-driven, correlated across multiple telemetry sources, and aligned with real-world SOC best practices used in healthcare environments.

---

## Organisational Overview

**Organisation Name:**  
England National Health Centre (ENHC)

**Industry:**  
Healthcare & Public Health Services

**Organisation Size:**  
Medium-sized healthcare organisation supporting clinical, administrative, and IT staff.

---

## Business Context

ENHC delivers critical healthcare and patient services and relies heavily on internal email systems, clinical workstations, and web-based applications. These systems process sensitive patient data, internal operational information, and staff credentials.

Due to the healthcare sector’s high value to threat actors, ENHC is a prime target for phishing campaigns, credential harvesting, and follow-on abuse of user access. Protecting endpoints, email infrastructure, and network communications is therefore a critical SOC priority.

---

## Introduction

This repository presents the final executive summary of a phishing-led security incident simulation conducted within ENHC.

### Objectives:
- Simulate a realistic phishing and credential harvesting attack
- Validate detection and response capabilities
- Demonstrate structured SOC investigation workflows
- Apply evidence-based correlation across telemetry sources

No alert was treated in isolation. All findings were validated using multiple data sources to reduce false positives and ensure investigative accuracy.

---

## Scope of Investigation

### In Scope
- Internal email delivery and user interaction
- Phishing link access and credential submission
- Endpoint telemetry and host-based activity
- Network traffic monitoring and DNS activity
- SOC investigation, response, and validation

### Out of Scope
- Cloud infrastructure
- Mobile devices
- Email gateway security platforms
- Third-party SaaS applications
- Full disk or memory forensics

---

## Tools & Telemetry Sources

The investigation relied on corroborated telemetry from multiple platforms:

- **GoPhish** – Phishing campaign delivery and user interaction tracking  
- **hMailServer** – Internal email services and mail log evidence  
- **Microsoft Defender for Endpoint (XDR)** – Endpoint protection, alerting, and automated investigation  
- **Windows Endpoint Telemetry (Sysmon)** – Process creation and network activity  
- **Splunk Enterprise** – Centralised log ingestion, correlation, and investigation  
- **pfSense Firewall** – Perimeter traffic visibility  
- **Suricata IDS** – Network intrusion detection and HTTP/DNS inspection  

---

## Investigation Methodology

The investigation followed a structured SOC lifecycle:

**Detection → Triage → Correlation → Investigation → Response → Review**

Email telemetry identified phishing delivery, which was correlated with user interaction data from GoPhish. Endpoint and network telemetry were analysed within defined time windows to confirm malicious activity and rule out false positives.

Manual investigation techniques were used to mirror real-world SOC operations, with workflows designed to be automation-ready for future SOAR integration.

---

## Detection & Analysis Approach

An evidence-based correlation model was applied:

- DNS queries reviewed for suspicious domain resolution  
- Source and destination IPs validated against campaign timelines  
- Port and protocol analysis performed (e.g., DNS 53, HTTPS 443)  
- Email delivery events correlated with user actions  
- Endpoint telemetry reviewed for execution, persistence, or payload delivery  

Time-bounded analysis ensured findings were accurate and context-aware.

---

## Artifacts & Evidence

### Indicators of Compromise (IOCs) & Forensic Artifacts

The following artifacts were reviewed and cross-validated:

- Phishing URLs accessed by ENHC users (Suricata HTTP & DNS logs)
- Source and destination IP addresses associated with outbound connections
- Ports and protocols indicating encrypted external communication
- Email sender identity and internal mailbox activity (hMailServer logs)
- Endpoint telemetry confirming user interaction without payload execution

All artifacts were correlated in Splunk to ensure no reliance on single-source alerts.

---

## MITRE ATT&CK Mapping

Observed activity was mapped to the MITRE ATT&CK framework:

- **T1566** – Phishing  
- **T1071.004** – Application Layer Protocol (HTTPS)  

No evidence of:
- Execution  
- Persistence  
- Privilege escalation  
- Lateral movement  

was identified during the investigation.

---

## Response & Containment Actions

Upon confirmation of credential harvesting activity, the following actions were taken:

- Impacted user credentials secured and reset
- Active sessions revoked
- Email activity reviewed for mailbox rule abuse
- Endpoint telemetry reviewed to confirm no payload execution
- Continued monitoring enabled for affected users and IP addresses
- Phishing awareness reinforcement for staff

No post-exploitation activity or lateral movement was observed.

---

## Mitigation & Hardening Measures

Post-incident actions focused on reducing future risk:

- Enforcement of Multi-Factor Authentication (MFA)
- Improved correlation across email, endpoint, and network logs
- Validation of endpoint integrity and credential exposure
- Refinement of SOC detection dashboards
- Reinforcement of internal phishing awareness controls

---

## Playbooks, Process & Operations

The investigation adhered to a repeatable SOC playbook:

**Detection → Triage → Correlation → Investigation → Response → Review**

While manual correlation was used, the workflow aligns with industry-standard SOC processes and supports future automation and scaling.

---

## MTTR & SOC Performance Metrics

- **Mean Time to Detect (MTTD):** Minutes after user interaction  
- **Mean Time to Investigate (MTTI):** ~40 minutes  
- **Mean Time to Respond (MTTR):** Within the same operational window  

---

## Lessons Learned

Aligned with NIST Cybersecurity Framework (CSF):

- **Identify:** Comprehensive telemetry coverage is essential  
- **Protect:** MFA significantly reduces credential abuse impact  
- **Detect:** Cross-source correlation increases confidence  
- **Respond:** Rapid containment prevents escalation  
- **Recover:** Continuous monitoring and process improvement close the loop  

---

## Recommendations & Future Improvements

- Implement enterprise email authentication (SPF, DKIM, DMARC)
- Expand conditional access policies for healthcare users
- Formalise SOC incident response playbooks and escalation paths
- Introduce automated alert correlation to reduce MTTR
- Enhance user reporting workflows for suspected phishing

---

## Final Summary

This project demonstrates ENHC’s SOC capability to detect, investigate, and respond to phishing-led threats using industry-standard tools and professional methodologies.

The investigation was structured, evidence-driven, and aligned with real-world healthcare SOC operations, reflecting mature Blue Team practices suitable for regulated environments.

