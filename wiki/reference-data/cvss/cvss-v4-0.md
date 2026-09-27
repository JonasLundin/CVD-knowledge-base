---
type: Metric
title: Common Vulnerability Scoring System (CVSS) v4.0
description: Next-generation vulnerability scoring standard introducing CVSS-B, CVSS-BT, CVSS-BE, and CVSS-BTE nomenclatures, separate Vulnerable/Subsequent system impacts, and Attack Requirements.
category: metric
tags:
- cvd
- metric
- scoring
- cvss-v4-0
- vulnerability-scoring
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
  provision: CVSS v4.0 Specification
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Common Vulnerability Scoring System (CVSS) Version 4.0** represents the next generation of the global vulnerability severity scoring standard, published in November 2023 by the Forum of Incident Response and Security Teams (FIRST)[^first-cvss-v4]. Designed to overcome the architectural constraints and operational misinterpretations of CVSS v3.1, CVSS v4.0 introduces substantial enhancements: fine-grained attack condition modeling, explicit separation between Vulnerable and Subsequent system impacts, formal human safety considerations, and a restructured scoring algorithm based on discrete MacroVectors and interpolated lookup tables[^iso-iec-29147].

CVSS v4.0 also resolves the industry-wide confusion between severity and risk by establishing mandatory nomenclature distinctions (CVSS-B, CVSS-BT, CVSS-BE, CVSS-BTE) that clarify whether a score reflects pure technical severity, active threat intelligence, or customized organizational environments.

# Technical Scope & Nomenclature Standard

To prevent consumers from equating unadjusted Base scores with real-world risk, CVSS v4.0 formally codifies four distinct score classifications:

```
+-----------------------------------------------------------------+
|                    CVSS v4.0 Nomenclature                       |
+-----------------------------------------------------------------+
                                |
         +----------------------+----------------------+
         |                                             |
         v                                             v
+-----------------------------+               +-----------------------------+
|           CVSS-B            |               |           CVSS-BT           |
| Base Metrics Alone          |               | Base + Threat Metrics       |
| (Intrinsic technical flaw)  |               | (Reflects active exploits)  |
+--------------+--------------+               +--------------+--------------+
               |                                             |
               v                                             v
+-----------------------------+               +-----------------------------+
|           CVSS-BE           |               |          CVSS-BTE           |
| Base + Environmental        |               | Base + Threat +             |
| (Modified for target asset) |               | Environmental (True Risk)   |
+-----------------------------+               +-----------------------------+
```

1. **CVSS-B**: Computed using only the Base metric group (assesses intrinsic technical severity).
2. **CVSS-BT**: Computed using Base and Threat metric groups (incorporates active threat intelligence and exploit maturity).
3. **CVSS-BE**: Computed using Base and Environmental metric groups (incorporates custom organizational mitigations and asset criticality).
4. **CVSS-BTE**: The comprehensive score incorporating Base, Threat, and Environmental metric groups, providing the closest approximation to actual operational risk.

# Detailed Metric Architecture & Enhancements

CVSS v4.0 revamps the metric structure to achieve higher fidelity and resolve persistent scoring ambiguities:

### 1. Separation of Attack Complexity and Attack Requirements
In CVSS v3.1, Attack Complexity conflated technical exploitation difficulty with execution prerequisites. CVSS v4.0 separates these concepts into two independent metrics:
- **Attack Complexity (AC)**: Reflects the presence of defensive security engineering (e.g., ASLR, DEP, memory tagging, cryptographic secrets) that the attacker must bypass: Low (`L`), High (`H`).
- **Attack Requirements (AT)**: Reflects deployment prerequisites or environmental conditions that must exist for the attack to succeed (e.g., race conditions, specific man-in-the-middle network placement, non-default configuration): None (`N`), Present (`P`).

### 2. User Interaction Granularity
CVSS v4.0 replaces the binary `UI:N/R` metric with a three-tier model:
- None (`N`): No interaction required.
- Passive (`P`): Requires involuntary or subverted interaction (e.g., visiting a malicious web page).
- Active (`A`): Requires explicit, targeted user cooperation (e.g., importing a malicious certificate, executing a downloaded file, ignoring security warnings).

### 3. Deconstruction of Scope into Dual Impact Systems
The ambiguous and controversial `Scope` metric from v3.1 is completely eliminated. In CVSS v4.0, impacts are evaluated across two explicitly decoupled domains:
- **Vulnerable System (VS)**: The software or hardware entity that contains the vulnerability:
  - Confidentiality (`VC`): None (`N`), Low (`L`), High (`H`).
  - Integrity (`VI`): None (`N`), Low (`L`), High (`H`).
  - Availability (`VA`): None (`N`), Low (`L`), High (`H`).
- **Subsequent System (SS)**: External software, hardware, networks, or cloud infrastructure that can be compromised downstream from the initial breach:
  - Confidentiality (`SC`): None (`N`), Low (`L`), High (`H`).
  - Integrity (`SI`): None (`N`), Low (`L`), High (`H`).
  - Availability (`SA`): None (`N`), Low (`L`), High (`H`).

### 4. Threat Metric Group (Exploit Maturity)
Replacing the legacy Temporal metrics, the Threat group focuses on dynamic adversarial activity:
- **Exploit Maturity (E)**: Unreported (`U`), Proof-of-Concept (`P`), Attacked (`A`), or Not Defined (`X`). When set to `A`, it indicates confirmed active exploitation in the wild.

### 5. Human Safety and Environmental Impact
In the Environmental group, CVSS v4.0 introduces the **Safety (S)** metric, allowing industrial control systems (ICS/SCADA), automotive, and medical device operators to model whether a cyber vulnerability could result in physical injury or loss of human life.

# Vector String Syntax & MacroVector Calculation

A complete CVSS v4.0 vector string articulates the expanded metric dimensions:

```
CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N
```

### The MacroVector Lookup Algorithm
Unlike previous versions that relied on continuous floating-point equations vulnerable to artificial score clustering, CVSS v4.0 calculates scores through a deterministic **MacroVector** system:
1. Metrics are grouped into six conceptual MacroVectors ($EQ_1$ through $EQ_6$).
2. Each MacroVector maps to an equivalence level representing its severity state.
3. The resulting 6-digit MacroVector (e.g., `[0, 1, 0, 2, 1, 0]`) indexes an expert-calibrated lookup table providing baseline numerical scores.
4. An interpolation algorithm adjusts the score based on the sub-metric values within the MacroVector group, producing a smooth, predictable 0.0 to 10.0 score.

# Practical Implementation in CVD Workflows

In modern PSIRT and vulnerability disclosure environments:
- **Dual Scoring during Transition**: PSIRTs authoring CVE Records and CSAF 2.0 advisories increasingly publish both CVSS v3.1 and CVSS v4.0 vector strings to support legacy and modern tooling concurrently.
- **CVE JSON 5.0 Integration**: CVSS v4.0 is natively supported in the `metrics` array under `cvssV4_0`:
  ```json
  "metrics": [
    {
      "format": "CVSS",
      "scenarios": [{"lang": "en", "value": "GENERAL"}],
      "cvssV4_0": {
        "version": "4.0",
        "vectorString": "CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N",
        "baseScore": 9.3,
        "baseSeverity": "CRITICAL"
      }
    }
  ]
  ```

# Dates and Transitions

- **November 1, 2023**: Official release and publication of the CVSS Version 4.0 Specification Document by FIRST.
- **2024–2026**: Ongoing phased adoption across commercial vulnerability scanners, government advisories (CISA, ENISA), and CVE Services.

# Related concepts

- [Reference Data Index](index.md)
- [CVSS v3.1 Specification](cvss-v3-1.md)
- [Exploit Prediction Scoring System (EPSS)](../epss/epss.md)
- [Stakeholder-Specific Vulnerability Categorization (SSVC)](../ssvc/ssvc.md)
- [CWE Reference Data](../cwe/cwe.md)
- [CNA Container](../../programmes/cve/record-format/cna-container.md)
- [ADP Container](../../programmes/cve/record-format/adp-container.md)
- [CVSS v4.0 Release Timeline](../../timeline/cvss-v4-release.md)

[^first-cvss-v4]: Forum of Incident Response and Security Teams (FIRST), Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0, https://www.first.org/cvss/v4-0/specification-document
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
