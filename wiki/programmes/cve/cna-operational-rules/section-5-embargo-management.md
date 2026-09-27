---
type: Rule
title: 'Section 5: Embargo Management and Coordination'
description: Operational rules governing CVE IDs in RESERVED state, confidential multi-party coordination, embargo windows, and leak response protocols under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-5-embargo-management
- embargo
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
- id: iso-iec-30111
  resource: https://www.iso.org/standard/72312.html
  title: "ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2019-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: Section 5
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 5: Embargo Management and Coordination** governs the confidentiality, sharing protocols, operational timelines, and leak-handling procedures for vulnerabilities held in the `RESERVED` state prior to public disclosure[^cve-program]. As codified in the CVE Numbering Authority (CNA) Operational Rules Version 4.0, an embargo provides a protected operational window allowing software vendors, open-source maintainers, and coordinators to develop, validate, and distribute security patches before adversaries can exploit the underlying flaws[^iso-iec-30111].

Under Section 5, reserving a CVE ID establishes a binding procedural expectation of confidentiality between the assigning CNA, the reporting researcher (finder), and collaborating downstream parties[^iso-iec-29147].

# Technical Scope & Embargo Lifecycle

The embargo lifecycle establishes a controlled progression from private reservation to synchronized public release:

```
+-----------------------------------------------------------------+
| 1. CVE ID Reservation & Embargo Initiation                      |
|    - CNA reserves ID via CVE Services API                       |
|    - Status: RESERVED (Metadata concealed)                      |
|    - Mutual agreement on target disclosure date (TDD)           |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| 2. Confidential Technical Remediation                           |
|    - Root-cause debugging, patch development, and testing       |
|    - Secure downstream pre-notification under NDA / embargo     |
+-------------------------------+---------------------------------+
                                |
             +------------------+------------------+
             | Regular Release                     | Premature Leak /
             | at TDD                              | In-the-Wild Exploit
             v                                     v
+-------------------------------+   +-------------------------------+
| 3. Synchronized Public Release|   | 4. Embargo Break Response     |
|    - Patch and advisory live  |   |    - Immediate embargo lift   |
|    - CVE Record PUBLISHED     |   |    - Emergency mitigations    |
|    - Coordinated announcement |   |    - Accelerated CVE publish  |
+-------------------------------+   +-------------------------------+
```

### Embargo Governance Principles

1. **Confidentiality of RESERVED IDs**: When a CNA assigns a reserved CVE ID to an unreleased vulnerability, the association between the identifier, the affected product, and the technical vulnerability details must remain confidential[^cve-program].
2. **Authorized Pre-Notification**: A CNA may share the assigned CVE ID and remediation details with trusted stakeholders (e.g., operating system distributors, cloud infrastructure providers, or national CSIRTs) strictly under bilateral embargo agreements or non-disclosure commitments to prepare synchronized patches[^iso-iec-29147].
3. **No Exploitation or weaponization**: Participating entities must never use embargoed vulnerability disclosures to develop offensive exploits, proprietary commercial intelligence, or competitive advantages[^cve-program].

# Embargo Windows and Extension Rules

Section 5 aligns with international disclosure norms regarding remediation timelines:

- **Standard Embargo Duration**: Standard industry disclosure windows typically range from **30 to 90 calendar days** following initial validation of the vulnerability report[^iso-iec-29147].
- **Mutual Agreement on Timelines**: The Target Disclosure Date (TDD) must be established through good-faith negotiation between the reporting finder and the affected vendor/CNA[^cve-program].
- **Embargo Extensions**: An extension beyond the standard window is permissible only when justified by exceptional technical complexity, such as:
  - Silicon-level hardware errata requiring microcode redesign;
  - Fundamental cryptographic protocol changes impacting international standards;
  - Complex multi-party dependencies affecting dozens of downstream platform vendors.
- **Prohibition of Unilateral Indefinite Embargos**: A vendor CNA may not unilaterally impose indefinite embargoes or delay disclosure indefinitely when a viable patch or mitigation is delayed due to commercial or product-roadmap prioritization[^cve-program].

# Embargo Breach Protocols ("Embargo Break")

If confidentiality is compromised prior to the agreed Target Disclosure Date, Section 5 triggers mandatory emergency procedures:

| Breach Scenario | Operational Trigger | Required CNA / Vendor Action |
| :--- | :--- | :--- |
| **Public Leak / PoC Release** | Functional exploit code or vulnerability details published on social media, public GitHub repositories, or security blogs. | Terminate embargo immediately; notify all coordinated parties; publish available workarounds and accelerate CVE record publication within 24 hours[^cve-program]. |
| **Active Exploitation (0-Day)** | Threat intelligence confirms active adversarial exploitation in production environments (e.g., CISA KEV listing). | Lift embargo immediately; issue emergency security advisory advising customers on detection and containment; publish CVE Record. |
| **Premature Advisory** | Downstream vendor accidentally publishes release notes referencing the CVE ID before the agreed embargo hour. | Coordinate accelerated release with the originating CNA; transition CVE ID to `PUBLISHED` status without waiting for original TDD. |

# Multi-Party & Cross-CNA Coordination

When an embargoed vulnerability resides in a shared dependency (e.g., an open-source library or common hardware chipset):
- **Lead Coordinator**: The affected parties should designate a primary coordinator (such as the upstream CNA, CERT/CC, CISA, or a national CSIRT under NIS2 Article 12)[^iso-iec-29147].
- **Secure Communication**: All technical information exchanges, diffs, and draft advisories must be transmitted using end-to-end cryptographic protection (e.g., OpenPGP encrypted email or authenticated, role-based coordination platforms)[^iso-iec-29147].
- **Synchronized Release**: All participating CNAs agree on a precise synchronized Universal Time Coordinated (UTC) release timestamp to prevent asymmetric exposure across timezones.

# Practical Implementation & PSIRT Workflow

In PSIRT operations:
1. **Embargo Registry**: The PSIRT maintains a secure internal database mapping Jira/Bugzilla tickets to `RESERVED` CVE IDs, associated finders, NDAs, and target disclosure dates.
2. **Access Control**: Source code commits containing vulnerability fixes are staged in private repositories with restricted developer access to prevent automated public commit scraping.
3. **Execution at TDD**: Upon reaching the synchronized UTC deadline, CI/CD pipelines merge public commits, push software packages to mirrors, publish the web advisory, and execute the CVE Services API call to publish the CVE Record.

# Dates and Transitions

- **CNA Rules Version 4.0 (March 2024)**: Codified formal obligations regarding the handling of RESERVED IDs and established explicit escalation channels for embargo disputes.
- **Coordination Alignment**: Incorporates procedural guidance from FIRST CVD Guidelines and ISO/IEC 29147:2018.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 1: Program Overview](section-1-program-overview.md)
- [Section 3: CVE ID Assignment Rules](section-3-id-assignment-rules.md)
- [Section 4: Record Publishing](section-4-record-publishing.md)
- [Section 6: Dispute Resolution](section-6-dispute-resolution.md)
- [Embargo Management Process](../../../process/embargo-management.md)
- [Multi-Party Coordination Process](../../../process/multi-party-coordination.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)
- [Coordinator Role](../../../roles/coordinator.md)
- [Finder Role](../../../roles/finder.md)
- [ISO/IEC 29147 Standard](../../../standards/iso-iec-29147.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
