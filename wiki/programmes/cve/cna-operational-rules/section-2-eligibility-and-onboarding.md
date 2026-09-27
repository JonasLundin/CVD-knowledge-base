---
type: Rule
title: 'Section 2: CNA Eligibility and Onboarding'
description: Eligibility criteria, application procedures, mandatory training, and ongoing compliance requirements for CVE Numbering Authorities under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-2-eligibility-and-onboarding
- onboarding
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
  provision: Section 2
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 2: CNA Eligibility and Onboarding** defines the institutional qualifications, formal onboarding pipeline, operational commitments, and status lifecycle for organizations seeking designation as a CVE Numbering Authority (CNA)[^cve-program]. As the CVE Program decentralizes vulnerability identification across global technology sectors, Section 2 provides the quality gating mechanisms required to ensure that prospective CNAs possess the operational maturity, technical capability, and procedural integrity necessary to assign CVE IDs and publish authoritative vulnerability data[^iso-iec-30111].

Under CNA Operational Rules Version 4.0, designation as a CNA is a formal operational partnership requiring sustained adherence to international vulnerability disclosure standards[^iso-iec-29147] and CVE Program policies.

# Technical Scope & Eligibility Criteria

To qualify for designation as a CNA, an applicant organization must satisfy rigorous organizational, procedural, and technical prerequisites:

### 1. Organizational Standing and Scope Demarcation
- **Legitimate Role**: The organization must be an active vendor, software publisher, open-source project steering committee, academic research entity, national CSIRT, or established vulnerability coordination platform[^cve-program].
- **Well-Defined Scope**: The applicant must submit a clearly bounded scope definition specifying the exact software, hardware, firmware, cloud services, or coordination domains for which it will assign CVE IDs[^cve-program]. Overlapping or ambiguous scopes that conflict with existing vendor CNAs are prohibited.

### 2. Operational Vulnerability Management Capability
- **Public Disclosure Channel**: The applicant must maintain a public-facing website, security portal, or repository release page where security advisories, fixed versions, and mitigation instructions are published[^iso-iec-29147].
- **Vulnerability Handling Process**: The organization must demonstrate an internal vulnerability response capability compliant with ISO/IEC 30111[^iso-iec-30111], including receipt mechanisms, triage workflows, patch authoring, and customer notification channels.
- **Secure Communication**: The applicant must maintain a published security intake channel (such as a monitored security mailbox or secure portal) supported by cryptographic protections (e.g., published PGP public keys or authenticated web forms)[^iso-iec-29147].

# Formal Onboarding Workflow

The CNA onboarding process is structured into five sequential phases administered by the designated Root CNA or the Secretariat:

```
+-----------------------------------------------------------------+
| 1. Application & Scope Proposal                                 |
|    - Submission of CNA Request Form                             |
|    - Definition of proposed technical scope                     |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| 2. Scoping Review & Vetting                                     |
|    - Root CNA reviews proposed scope against existing registry  |
|    - Verification of ISO/IEC 29147 disclosure policy            |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| 3. Mandatory Training Curriculum                                |
|    - Section 3: Assignment & Counting Rules                     |
|    - Section 4: Record Formatting & CVE JSON 5.0 Schemas        |
|    - Section 5: Embargo & RESERVED State Rules                  |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| 4. Operational Gating & Test Verification                       |
|    - CVE Services API onboarding (orgId, admin credentials)     |
|    - Test environment sandbox submission of populated records   |
|    - Root validation of JSON syntax and mandatory elements      |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| 5. Designation & Public Announcement                            |
|    - Execution of CNA Terms of Use agreement                    |
|    - Production CVE Services credentials issued                 |
|    - Official listing published on cve.org                      |
+-----------------------------------------------------------------+
```

### Onboarding Steps and Requirements

1. **Application Submission**: The candidate submits a formal charter detailing corporate identity, point-of-contact (PoC) email addresses, PGP keys, public advisory URL, and the proposed scope statement[^cve-program].
2. **Review and Mentorship**: The governing Root CNA evaluates the application to prevent scope overlaps with existing CNAs. If accepted, the Root assigns a mentor to guide the candidate.
3. **Training Modules**: Nominated representatives must complete the CVE Program Training Curriculum, covering ID reservation, assignment counting logic, CVE JSON 5.0 schema requirements, and embargo management[^cve-program].
4. **Practical Assessment**: The candidate generates and validates test CVE Records in the CVE Services Test Environment. The Root verifies that records adhere to JSON schema constraints, containing proper descriptions, affected version ranges, problem types (CWEs), and references[^cve-program].
5. **Designation**: Upon successful review, the Root issues production credentials (`orgId` and API keys) via the CVE Services API, and the Secretariat publishes the new CNA on the global roster.

# Ongoing Compliance & Status Lifecycle

Maintaining CNA status requires ongoing adherence to operational benchmarks established in Section 2:

- **Active Point of Contact**: The CNA must maintain functional, monitored PoCs. Inquiries from Root CNAs, finders, or the Secretariat must receive an initial acknowledgement within specified operational timeframes (typically within 30 calendar days)[^cve-program].
- **Timely Record Publishing**: The CNA must consistently publish records for all publicly disclosed vulnerabilities in accordance with Section 4 timelines. Leaving disclosed issues in RESERVED status is grounds for review[^cve-program].
- **Status Classifications**:
  - **Active**: The CNA actively assigns IDs, publishes records, responds to communications, and complies with all rules.
  - **Inactive / Suspended**: A CNA experiencing organizational disruptions, unresolved communication failures, or chronic assignment violations may be placed in Inactive status. During suspension, the Root assumes responsibility for assignment within that scope[^cve-program].
  - **De-designation / Offboarding**: If a CNA fails to remediate deficiencies, undergoes corporate dissolution, or requests voluntary retirement, the Secretariat revokes its credentials. The governing Root either absorbs the scope or reassigns it to another authority[^cve-program].

# Applicability & Practical Implementation

For enterprise PSIRT operations, achieving and maintaining CNA status yields significant strategic advantages:
- **Autonomous Identifier Control**: Vendors can reserve blocks of CVE IDs in advance, assigning IDs during early development and triage phases without relying on third-party coordinators.
- **Synchronized Disclosure**: Vendors control the transition from RESERVED to PUBLISHED, ensuring that public CVE Records synchronize perfectly with security bulletins, firmware releases, and CSAF advisory distribution[^iso-iec-29147].
- **Audit Readiness**: Maintaining CNA compliance provides documented evidence of formal vulnerability handling processes, supporting conformity assessments under emerging regulatory frameworks such as the EU Cyber Resilience Act (CRA)[^iso-iec-30111].

# Dates and Transitions

- **March 1, 2024**: Entry into force of CNA Operational Rules Version 4.0, which formalized structured training requirements, automated onboarding via the CVE Services API, and clear inactive/offboarding criteria.
- **CVE Services API v2.1+**: Current production API standard utilized for automated organizational onboarding, user management, and quota administration.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 1: Program Overview](section-1-program-overview.md)
- [Section 3: CVE ID Assignment Rules](section-3-id-assignment-rules.md)
- [Section 4: Record Publishing](section-4-record-publishing.md)
- [Section 5: Embargo Management](section-5-embargo-management.md)
- [Section 6: Dispute Resolution](section-6-dispute-resolution.md)
- [CNA Role](../../../roles/cna.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)
- [Secretariat Role](../../../roles/secretariat.md)
- [ISO/IEC 29147 Standard](../../../standards/iso-iec-29147.md)
- [ISO/IEC 30111 Standard](../../../standards/iso-iec-30111.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
