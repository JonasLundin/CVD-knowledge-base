---
type: Metric
title: Stakeholder-Specific Vulnerability Categorization (SSVC)
description: Role-tailored decision-tree framework authored by Carnegie Mellon SEI and CISA that prioritizes vulnerability remediation based on exploitation, exposure, and mission impact.
category: metric
tags:
- cvd
- metric
- scoring
- ssvc
- decision-tree
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
  provision: CISA/SEI SSVC
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Stakeholder-Specific Vulnerability Categorization (SSVC)** is a conceptual framework and decision-tree methodology created by the Software Engineering Institute (SEI) at Carnegie Mellon University in partnership with the Cybersecurity and Infrastructure Security Agency (CISA)[^first-cvss-v4]. Departing fundamentally from continuous numerical scoring systems like CVSS, SSVC evaluates vulnerabilities through qualitative, contextual decision trees tailored to the specific role of the decision-maker—categorizing actions into discrete operational outcomes: **Track**, **Track\***, **Attend**, or **Act**[^iso-iec-29147].

SSVC addresses the core structural flaw of traditional vulnerability management: that a vulnerability's urgency depends on the stakeholder's context. A software developer (Supplier), an enterprise IT department (Deployer), and a national CSIRT (Coordinator) require fundamentally different operational decisions when confronted with the same CVE.

# Technical Scope & The Stakeholder Perspectives

SSVC defines distinct decision trees tailored to three primary operational roles:

1. **Deployer Tree**: Geared toward enterprise IT administrators, asset owners, and CISOs who must decide when and how quickly to install a patch across production infrastructure.
2. **Supplier Tree**: Geared toward software vendors and open-source maintainers who must prioritize developer engineering sprints, patch authoring, and backporting.
3. **Coordinator Tree**: Geared toward national CERTs/CSIRTs (e.g., CERT/CC, CISA, national coordinators under NIS2 Article 12) managing multi-party disclosure, embargo timelines, and public advisories.

# CISA Deployer Decision Tree & Decision Points

The CISA SSVC model for enterprise deployers evaluates four sequential decision points to arrive at an action recommendation:

```
                      +---------------------------------------+
                      |             Vulnerability             |
                      +-------------------+-------------------+
                                          |
                                          v
                      +---------------------------------------+
                      |         1. Exploitation State         |
                      |        [None / PoC / Active]          |
                      +-------------------+-------------------+
                                          |
                                          v
                      +---------------------------------------+
                      |            2. Automatable?            |
                      |              [Yes / No]               |
                      +-------------------+-------------------+
                                          |
                                          v
                      +---------------------------------------+
                      |         3. Technical Impact           |
                      |          [Partial / Total]            |
                      +-------------------+-------------------+
                                          |
                                          v
                      +---------------------------------------+
                      |     4. Mission / Well-being Impact    |
                      |          [Low / Medium / High]        |
                      +-------------------+-------------------+
                                          |
                                          v
       +------------------+------------------+------------------+
       |                  |                  |                  |
       v                  v                  v                  v
   [ Track ]          [ Track* ]        [ Attend ]           [ Act ]
  Standard Cycle    Monitor Closely   Accelerated SLA    Immediate Emergency
```

### The Four Decision Points

1. **Exploitation**:
   - `None`: No evidence of active exploit code or in-the-wild attacks.
   - `PoC` (Proof of Concept): Functional exploit code or technical demonstration is publicly accessible.
   - `Active`: Verified threat actor exploitation in production environments (e.g., KEV listing).
2. **Automatable**:
   - `Yes`: Attackers can reliably automate scanning, weaponization, and exploitation over network boundaries without human victim interaction (e.g., wormable RCEs, automated credential stuffing).
   - `No`: Exploitation requires targeted manual attacker interaction, complex pre-conditions, or victim social engineering.
3. **Technical Impact**:
   - `Partial`: Exploit achieves limited disclosure, denial of service, or restricted privilege escalation.
   - `Total`: Complete takeover of the vulnerable system, kernel-level execution, or full administrative control.
4. **Mission Prevalence / Well-being**:
   - Evaluates the critical nature of the affected host to the organization's core operations or human health and safety (Minimal, Support, Essential).

# The Four Action Outcomes

The decision tree terminates in one of four actionable operational outcomes:

| Decision Outcome | Operational Meaning | Recommended Remediation SLA |
| :--- | :--- | :--- |
| **Track** | Routine vulnerability posing negligible immediate operational risk. | Remediate during standard, scheduled maintenance windows (e.g., monthly patch cycle). |
| **Track\*** | Low immediate risk, but possessing characteristics (such as high technical impact) that could escalate rapidly if exploit status changes. | Monitor threat feeds closely; remediate in next scheduled cycle or earlier if PoC appears. |
| **Attend** | Significant threat requiring accelerated operational attention. | Remediate faster than standard cycle (e.g., within 14 to 30 days), deploying temporary mitigations if patches are pending. |
| **Act** | Critical emergency presenting immediate danger to mission operations. | Immediate mobilization of incident response teams; emergency patch deployment or asset isolation within 24–72 hours. |

# Practical Implementation in Enterprise PSIRT & SOC

### Embedding SSVC in CVE JSON 5.0 and ADP Containers

CISA ADP actively evaluates new CVEs using SSVC decision trees, embedding the structured decision into the `adp` container:

```json
{
  "other": {
    "type": "ssvc",
    "content": {
      "timestamp": "2026-02-14T08:30:00.000Z",
      "id": "CVE-2026-10492",
      "role": "CISA Coordinator",
      "options": [
        {"Exploitation": "active"},
        {"Automatable": "yes"},
        {"Technical Impact": "total"}
      ],
      "decision": "Act"
    }
  }
}
```

### Automation via Open-Source Calculators

Security orchestration platforms execute SSVC logic using open-source Python packages (`ssvc-calc`), evaluating CMDB asset tags to determine Mission Prevalence dynamically and routing high-priority Jira tickets directly to engineering squads when a CVE evaluates to `Act`.

# Dates and Transitions

- **2019**: Initial publication of the SSVC conceptual framework by Carnegie Mellon SEI.
- **November 2020**: CISA officially adopted SSVC, publishing customized decision trees for government and critical infrastructure deployers.
- **2022–2024**: SSVC integrated natively into CVE JSON Schema 5.0 ADP blocks and CISA Vulnrichment feeds.

# Related concepts

- [Reference Data Index](index.md)
- [CVSS v3.1 Specification](cvss-v3-1.md)
- [CVSS v4.0 Specification](cvss-v4-0.md)
- [Exploit Prediction Scoring System (EPSS)](epss.md)
- [CISA KEV Catalog](kev.md)
- [ADP Container](../programmes/cve/record-format/adp-container.md)
- [Vendor PSIRT Role](../roles/vendor-psirt.md)

[^first-cvss-v4]: Forum of Incident Response and Security Teams (FIRST), Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0, https://www.first.org/cvss/v4-0/specification-document
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
