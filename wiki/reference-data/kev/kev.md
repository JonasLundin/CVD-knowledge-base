---
type: Metric
title: CISA Known Exploited Vulnerabilities (KEV) Catalog
description: Authoritative catalog of vulnerabilities known to be actively exploited
  in the wild, carrying mandatory federal remediation deadlines.
category: metric
tags:
- cvd
- metric
- cisa
- kev
- threat-intelligence
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-cvss-v4
  resource: https://www.first.org/cvss/v4-0/specification-document
  title: Common Vulnerability Scoring System (CVSS) Specification Document Version
    4.0
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2023-11-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CISA Binding Operational Directive 22-01
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Known Exploited Vulnerabilities (KEV) Catalog** is an authoritative, publicly accessible register established by the US Cybersecurity and Infrastructure Security Agency (**CISA**) under **Binding Operational Directive 22-01 (BOD 22-01)**[^first-cvss-v4].

KEV shifts vulnerability management from theoretical severity (e.g. CVSS 9.0+) to empirical evidence of malicious exploitation, cataloging vulnerabilities that threat actors are actively leveraging in attacks worldwide.

# Inclusion Thresholds & Operational Mandates

### 1. Mandatory Addition Criteria
For a CVE to be added to the KEV catalog, CISA requires three strict conditions:
1. The vulnerability has been assigned an official CVE ID.
2. There is reliable, corroborated evidence of active exploitation in the wild.
3. There is a clear remediation action (vendor patch or mitigation guidance).

### 2. BOD 22-01 Federal Remediation Deadlines
- For zero-day vulnerabilities actively exploited prior to patch release: Remediation typically mandated within **14 days**.
- For standard disclosed vulnerabilities: Remediation typically mandated within **21 days**.

# Impact on SSVC and Risk Prioritization

A vulnerability's presence in KEV automatically changes its decision state across risk engines:
- In **SSVC**, the *Exploitation* branch immediately evaluates to `Active`, elevating the decision outcome to `Act` or `Attend`.
- In enterprise SOC/VM programs, KEV status triggers immediate emergency patching playbooks.

# Related concepts
- [Stakeholder-Specific Vulnerability Categorization (SSVC)](../ssvc/ssvc.md)
- [Exploit Prediction Scoring System (EPSS)](../epss/epss.md)
- [ADP Container](../../programmes/cve/record-format/adp-container.md)

[^first-cvss-v4]: Forum of Incident Response and Security Teams (FIRST), Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0, https://www.first.org/cvss/v4-0/specification-document
