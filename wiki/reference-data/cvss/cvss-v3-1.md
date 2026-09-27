---
type: Metric
title: Common Vulnerability Scoring System (CVSS) v3.1
description: Quantitative severity scoring specification evaluating base, temporal, and environmental metric groups to assess software vulnerability characteristics.
category: metric
tags:
- cvd
- metric
- scoring
- cvss-v3-1
- severity-assessment
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-cvss-v4
  resource: https://www.first.org/cvss/v4-0/specification-document
  title: Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2023-11-01T00:00:00Z'
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CVSS v3.1 Specification
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Common Vulnerability Scoring System (CVSS) Version 3.1** is an open, industry-standard scoring specification maintained by the Forum of Incident Response and Security Teams (FIRST) to assess and communicate the fundamental technical severity of information technology vulnerabilities[^first-cvss-v4]. Adopted globally across security advisories, vulnerability scanners, and compliance frameworks, CVSS v3.1 provides an objective, repeatable methodology to compute numerical severity scores ranging from 0.0 to 10.0[^iso-iec-29147].

CVSS v3.1 is explicitly designed to measure technical severity—the intrinsic difficulty and direct impact of an exploit—rather than dynamic threat likelihood or enterprise risk. In vulnerability disclosure, CVSS v3.1 vector strings serve as universal shorthand for communicating exploit constraints and impact boundaries.

# Technical Scope & Metric Architecture

The CVSS v3.1 framework partitions vulnerability evaluation into three structured metric groups:

```
+-----------------------------------------------------------------+
|                       CVSS v3.1 Framework                       |
+-----------------------------------------------------------------+
                                |
         +----------------------+----------------------+
         |                      |                      |
         v                      v                      v
+-----------------+    +-----------------+    +-----------------+
|   Base Group    |    | Temporal Group  |    |  Environmental  |
| (Intrinsic to   |    | (Changes over   |    | (Specific to an |
|  vulnerability) |    |  time: exploit  |    |  organization's |
|                 |    |  code maturity) |    |  environment)   |
+--------+--------+    +--------+--------+    +--------+--------+
         |                      |                      |
         +----------------------+----------------------+
                                |
                                v
               +---------------------------------+
               |   Numerical Score (0.0 - 10.0)  |
               |   & Qualitative Severity Rating |
               +---------------------------------+
```

### 1. Base Metric Group
The Base group captures the unalterable qualities of a vulnerability across two main sub-vectors:

#### Exploitability Metrics
- **Attack Vector (AV)**: Contextual boundary from which exploitation is possible: Network (`N`: 0.85), Adjacent (`A`: 0.62), Local (`L`: 0.55), Physical (`P`: 0.20).
- **Attack Complexity (AC)**: Conditions beyond the attacker's control required to execute the exploit: Low (`L`: 0.77), High (`H`: 0.44).
- **Privileges Required (PR)**: Level of authentication necessary before launching the attack:
  - Scope Unchanged: None (`N`: 0.85), Low (`L`: 0.62), High (`H`: 0.27).
  - Scope Changed: None (`N`: 0.85), Low (`L`: 0.68), High (`H`: 0.50).
- **User Interaction (UI)**: Necessity of a human victim taking an action: None (`N`: 0.85), Required (`R`: 0.62).
- **Scope (S)**: Indicates whether the vulnerability can impact resources beyond the authorization privileges managed by the security authority of the vulnerable component: Unchanged (`U`), Changed (`C`).

#### Impact Metrics
- **Confidentiality Impact (C)**: Loss of data privacy: None (`N`), Low (`L`), High (`H`).
- **Integrity Impact (I)**: Loss of data trustworthiness or unauthorized modification: None (`N`), Low (`L`), High (`H`).
- **Availability Impact (A)**: Disruption of access or service degradation: None (`N`), Low (`L`), High (`H`).

### 2. Qualitative Severity Ratings

CVSS v3.1 maps computed numerical Base scores to standardized qualitative bands:

| Numerical Score Range | Qualitative Severity Rating |
| :--- | :--- |
| **0.0** | None |
| **0.1 – 3.9** | Low |
| **4.0 – 6.9** | Medium |
| **7.0 – 8.9** | High |
| **9.0 – 10.0** | Critical |

# Vector String Syntax & Calculation Formula

A CVSS v3.1 score is communicated alongside a standardized vector string formatted with slash-separated metric keys:

```
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

### Base Score Formula Highlights
The Base score is computed by combining Exploitability and Impact sub-scores:
1. **Impact Sub-score ($ISC$)**:
   $$\text{ISCBase} = 1 - [(1 - \text{Impact}_C) \times (1 - \text{Impact}_I) \times (1 - \text{Impact}_A)]$$
   If Scope is Unchanged: $\text{Impact} = 6.42 \times \text{ISCBase}$.  
   If Scope is Changed: $\text{Impact} = 7.52 \times (\text{ISCBase} - 0.029) - 3.25 \times (\text{ISCBase} - 0.02)^{15}$.
2. **Exploitability Sub-score ($ESC$)**:
   $$\text{Exploitability} = 8.22 \times \text{AV} \times \text{AC} \times \text{PR} \times \text{UI}$$
3. **Overall Base Score**:
   - If $\text{Impact} \le 0$: Base Score is $0.0$.
   - If Scope Unchanged: $\text{BaseScore} = \text{Roundup}(\min(\text{Impact} + \text{Exploitability}, 10))$.
   - If Scope Changed: $\text{BaseScore} = \text{Roundup}(\min(1.08 \times (\text{Impact} + \text{Exploitability}), 10))$.

# Limitations & The Evolution to CVSS v4.0

Despite its widespread adoption, industry operational experience revealed critical limitations in CVSS v3.1 that drove the development of CVSS v4.0[^first-cvss-v4]:
- **Severity vs. Risk Confusion**: Consumers frequently treat CVSS Base scores as risk scores, leading to patch fatigue by treating all 9.8 vulnerabilities as equally urgent, even when no exploit exists in the wild.
- **Ambiguity in the Scope Metric**: The `Scope: Changed` definition created extensive debate among analysts regarding whether a guest-to-host VM escape, microservice call, or database injection warranted a Scope change.
- **Inability to Model OT/ICS Safety**: CVSS v3.1 evaluates only CIA (Confidentiality, Integrity, Availability), failing to represent operational technology impacts such as physical device damage or human safety hazards.
- **Conflation of Attack Conditions**: High Attack Complexity was frequently misapplied to vulnerabilities that simply required specific network topologies rather than specialized cryptographic or timing race capabilities.

# Practical Implementation in CVD Workflows

In Coordinated Vulnerability Disclosure (CVD) operations:
- **Triage Assessment**: Product Security Incident Response Teams (PSIRTs) score incoming reports using CVSS v3.1 to establish initial SLA handling windows.
- **Machine-Readable Publishing**: CVSS v3.1 vectors are embedded directly into CVE JSON 5.0 (`metrics[].cvssV3_1`) and CSAF 2.0 (`vulnerabilities[].scores[].cvss_v3`) records.

# Dates and Transitions

- **June 2019**: Official release of CVSS Version 3.1 by FIRST, clarifying scoring guidance without altering mathematical formulas.
- **November 2023**: Launch of CVSS Version 4.0, initiating a gradual multi-year industry transition. CVSS v3.1 remains widely used across legacy toolsets.

# Related concepts

- [Reference Data Index](index.md)
- [CVSS v4.0 Specification](cvss-v4-0.md)
- [Exploit Prediction Scoring System (EPSS)](../epss/epss.md)
- [Stakeholder-Specific Vulnerability Categorization (SSVC)](../ssvc/ssvc.md)
- [CWE Reference Data](../cwe/cwe.md)
- [CNA Container](../../programmes/cve/record-format/cna-container.md)
- [CSAF Security Advisory](../../formats/csaf/csaf-security-advisory.md)

[^first-cvss-v4]: Forum of Incident Response and Security Teams (FIRST), Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0, https://www.first.org/cvss/v4-0/specification-document
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
