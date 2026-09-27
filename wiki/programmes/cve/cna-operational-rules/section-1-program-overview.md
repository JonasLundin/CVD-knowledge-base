---
type: Rule
title: 'Section 1: CNA Program Overview and Scope'
description: Foundational principles, governance hierarchy, operational scope, and structural responsibilities of the CVE Numbering Authority program under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-1-program-overview
- governance
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-program
  resource: https://www.cve.org/ResourcesSupport/AllResources/CNARules
  title: CVE Numbering Authority (CNA) Operational Rules Version 4.0
  author: CVE Program / The MITRE Corporation
  last_modified: '2024-03-01T00:00:00Z'
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: Section 1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 1: CNA Program Overview and Scope** establishes the foundational governance architecture, core mission, and operational structure of the Common Vulnerabilities and Exposures (CVE) Program[^cve-program]. As codified in Version 4.0 of the CVE Numbering Authority (CNA) Operational Rules, the CVE Program operates as a federated international standard for identifying, defining, and cataloging publicly known cybersecurity vulnerabilities.

The primary objective of Section 1 is to ensure consistent, non-duplicative, and vendor-neutral vulnerability identification across global IT, OT, cloud, open-source, and IoT ecosystems[^iso-iec-29147]. By establishing clear boundaries for organizational authority, Section 1 prevents conflicting vulnerability identifiers and empowers designated entities to assign CVE IDs and publish authoritative CVE Records.

# Technical Scope & Governance Hierarchy

The CVE Program functions through a hierarchical, federated delegation model comprising distinct organizational tiers:

```
                  +--------------------------------+
                  |           CVE Board            |
                  |     (Strategic Governance)     |
                  +---------------+----------------+
                                  |
                  +---------------+----------------+
                  |         Secretariat            |
                  |   (Operational Management)     |
                  +---------------+----------------+
                                  |
         +------------------------+------------------------+
         |                                                 |
+--------+-------+                                 +-------+--------+
| Top-Level Root |                                 | Top-Level Root |
|  (e.g., CISA)  |                                 | (e.g., MITRE)  |
+--------+-------+                                 +-------+--------+
         |                                                 |
+--------+-------+                                 +-------+--------+
|      Root      |                                 |      Root      |
| (e.g., Red Hat)|                                 | (e.g., ENISA)  |
+--------+-------+                                 +-------+--------+
         |                                                 |
+--------+-------+--------+                       +--------+-------+--------+
| CNA: Vendor A  | CNA: B |                       | CNA: Vendor C  | CNA: D |
+----------------+--------+                       +----------------+--------+
```

### Hierarchy Tiers and Responsibilities

1. **CVE Board**: The independent, multi-stakeholder governing body that oversees program policies, operational rules, strategic direction, and dispute arbitrations. Members represent vendors, researchers, government agencies, coordinators, and academia[^cve-program].
2. **Secretariat**: Manages day-to-day administrative operations, infrastructure maintenance (such as CVE Services and the central registry), CNA onboarding pipelines, meeting facilitation, and official documentation (currently administered by The MITRE Corporation)[^cve-program].
3. **Top-Level Roots (TL-Roots)**: Designated organizations responsible for managing large portions of the CVE ecosystem across specific domains, sectors, or sovereign geographical areas (e.g., CISA for civilian government and US critical infrastructure, MITRE for general commercial and international spaces, and ENISA within the EU context)[^cve-program].
4. **Roots**: Organizations appointed by a TL-Root or Secretariat to manage a sub-federation of CNAs. Roots oversee onboarding, training, mentoring, quality assurance, and scope-boundary enforcement for the CNAs within their designated hierarchy[^cve-program].
5. **CVE Numbering Authorities (CNAs)**: Authorized organizations granted direct authority to assign CVE IDs and author CVE Records for vulnerabilities within their pre-defined scope[^cve-program].
6. **Authorized Data Publishers (ADPs)**: Specialized organizations permitted to enrich existing CVE Records by injecting supplementary data (such as scoring metrics, CWE tags, affected versions, or references) into dedicated ADP containers without altering the CNA's primary record[^cve-program].

# Scope Definition and Typologies

Every CNA possesses a documented, publicly registered "Scope" that defines the precise technology products, services, repositories, or coordination boundaries within which it may allocate CVE IDs. Section 1 classifies CNAs into key functional scopes:

| CNA Scope Type | Operational Focus | Typical Organizations | Permitted Assignment Boundary |
| :--- | :--- | :--- | :--- |
| **Vendor / Producer CNA** | First-party proprietary hardware, software, cloud services, and firmware. | Microsoft, Apple, Cisco, Siemens, Oracle. | Strictly limited to products authored, owned, or maintained by the vendor. |
| **Open Source Project CNA** | Community-maintained software projects, libraries, and runtime ecosystems. | Apache Software Foundation, Linux Kernel, Python Software Foundation. | Open-source repositories and packages under the project's governance. |
| **National / Regional Coordinator CNA** | Multi-vendor vulnerabilities, third-party disclosures, and uncoordinated findings within a territorial jurisdiction. | CERT/CC, JPCERT/CC, CISA, BSI, CERT-EU. | Third-party software affecting domestic constituents or vendors lacking their own CNA. |
| **Third-Party / Bug Bounty / Researcher CNA** | Vulnerabilities discovered by researchers or hosted on triage platforms. | HackerOne, Bugcrowd, Snyk, VulDB. | Disclosures where the affected vendor is not a CNA and agrees to coordination. |
| **Root CNA** | Oversight and backup assignment authority for subordinate CNAs and orphaned vendors. | Red Hat, CISA, ENISA. | Entire designated sub-ecosystem or escalated multi-vendor disputes. |

# Operational Requirements & Core Rules

Section 1 mandates key operational covenants for all participating entities:

- **Neutrality and Impartiality**: CNAs must assign CVE IDs based strictly on technical qualification without using CVE assignments as punitive measures, commercial leverage, or public shaming tools[^cve-program].
- **Anti-Duplication Principle**: A single vulnerability must receive exactly one CVE ID. CNAs are forbidden from minting duplicate identifiers for vulnerabilities already assigned a valid CVE ID by upstream maintainers or peer CNAs[^cve-program].
- **Adherence to CNA Operational Rules**: Any organization serving as a CNA must formally agree to abide by the current published version of the CNA Operational Rules. Failure to maintain compliance can result in remediation plans, temporary suspension, or revocation of CNA designation[^cve-program].
- **No Licensing Fees**: CVE IDs, CVE Records, and CVE Services API access must remain freely accessible and unencumbered by intellectual property restrictions or licensing fees for finders, vendors, and the public[^cve-program].

# Applicability & Practical Implementation

### Practical Integration for PSIRTs

When an enterprise product security incident response team (PSIRT) establishes a CNA under Section 1 rules:
1. **Scope Boundaries**: The PSIRT documents every product family under its corporate control. Vulnerabilities identified in bundled third-party commercial components must not be assigned under the vendor's first-party scope unless the vendor maintains a custom, branched fork with unique vulnerabilities[^cve-program].
2. **Interface with CVD Policies**: The CNA charter integrates directly with the vendor's ISO/IEC 29147 disclosure policy, publishing the CNA's official contact points, PGP keys, and assignment workflows in `security.txt` and public security portals[^iso-iec-29147].
3. **API Credentials**: The CNA receives administrative credentials to the CVE Services API, enabling automated reservation of ID blocks and direct JSON 5.0 record publication.

# Dates and Transitions

- **CNA Rules Version 4.0**: Formally adopted and promulgated on March 1, 2024, superseding Version 3.0.
- **Mandatory JSON 5.0 Migration**: In conjunction with the transition to Rules v4.0, all CNAs were required to publish records exclusively using the CVE JSON Schema Version 5.0 format via the CVE Services API, ending legacy CVE flat-file and JSON 4.0 submissions.
- **Root Federation Expansion**: Ongoing operational rollout delegating additional continental and national Roots (such as ENISA's designation as a Root) under the federated governance model.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 2: Eligibility and Onboarding](section-2-eligibility-and-onboarding.md)
- [Section 3: CVE ID Assignment Rules](section-3-id-assignment-rules.md)
- [Section 4: Record Publishing](section-4-record-publishing.md)
- [Section 5: Embargo Management](section-5-embargo-management.md)
- [Section 6: Dispute Resolution](section-6-dispute-resolution.md)
- [CVE Program Overview](../../cve-program.md)
- [CNA Role](../../../roles/cna.md)
- [Secretariat Role](../../../roles/secretariat.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)
- [Coordinator Role](../../../roles/coordinator.md)
- [Authorized Data Publisher Role](../../../roles/authorized-data-publisher.md)
- [ISO/IEC 29147 Standard](../../../standards/iso-iec-29147.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
