---
type: Rule
title: 'Section 3: CVE ID Assignment Rules'
description: Technical qualification criteria, counting logic, independent fixability principles, and scoping boundaries governing CVE ID assignments under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-3-id-assignment-rules
- counting-rules
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
  provision: Section 3
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 3: CVE ID Assignment Rules** forms the core technical standard of the CVE Numbering Authority (CNA) Operational Rules Version 4.0[^cve-program]. It codifies the precise definition of a cybersecurity vulnerability, dictates qualification benchmarks, and establishes binding counting rules used to determine whether reported software weaknesses warrant one or multiple unique CVE identifiers[^iso-iec-30111].

The integrity of global vulnerability management depends on strict adherence to Section 3. Consistent assignment logic prevents "identifier inflation" (assigning multiple IDs to a single bug) as well as "identifier conflation" (merging independent security defects under a single ID), ensuring that security operations centers, asset owners, and automated scanners can track and remediate vulnerabilities accurately[^iso-iec-29147].

# Technical Scope & Vulnerability Definition

Under Section 3 of the CNA Rules, a candidate issue qualifies for CVE ID assignment only if it meets the formal definition of a vulnerability and satisfies product qualification tests:

### 1. Definition of a Vulnerability
A vulnerability is defined as a flaw in a computational logic (source code, firmware, hardware design, or protocol specification) found in software, firmware, hardware, or service components that can be exploited by an adversary to violate implicit or explicit security policies[^cve-program]. Security policy violations include:
- Execution of unauthorized code or system commands;
- Unauthorized access, disclosure, modification, or destruction of sensitive data;
- Circumvention of authentication, authorization, or access control mechanisms;
- Induction of unintended denial-of-service (DoS) conditions impacting availability.

### 2. Qualification Criteria
To receive a CVE ID, the vulnerability must:
- **Be in a generally available or widely deployed product**: Publicly distributed software, open-source repositories, commercial hardware, or public cloud endpoints. Purely custom, internal-only enterprise software does not receive a CVE ID unless the vendor makes the vulnerability information public[^cve-program].
- **Be independently fixable or acknowledgeable**: The product vendor or maintainer must be capable of producing an update, workaround, or formal security advisory addressing the defect[^cve-program].
- **Be distinct from operational misconfiguration**: Administrative errors, insecure environment tuning, or deliberate weakening of security by a root administrator do not qualify, unless the product documentation explicitly recommended the insecure configuration or the software default state is inherently unsafe[^cve-program].
- **End-of-Life (EOL) Software**: Discontinued or unsupported products remain eligible for CVE assignment if the vulnerability affects software that was once generally available. The record must indicate the unsupported status[^cve-program].

# CVE Counting Rules & Decision Logic

Section 3 establishes rigorous counting rules to determine the exact number of CVE IDs required when evaluating security reports:

```
                          +-------------------------------+
                          |    Candidate Vulnerability    |
                          +---------------+---------------+
                                          |
                                          v
                          +---------------+---------------+
                          |  Meets Qualification Criteria?|
                          +-------+---------------+-------+
                                  | No            | Yes
                                  v               v
                           [Do Not Assign]   +----+--------------------------+
                                             | Independent Fixability Test:  |
                                             | Can Bug A be fixed without    |
                                             | fixing Bug B?                 |
                                             +----+--------------------+-----+
                                                  | Yes                | No
                                                  v                    v
                                          +-------+-------+    +-------+-------+
                                          | Assign 2+ IDs |    | Single Origin |
                                          | (Distinct     |    | Flaw?         |
                                          | Defects)      |    +---+-------+---+
                                          +---------------+        |       |
                                                             Yes   |       | No
                                                                   v       v
                                                          [Assign 1 ID] [Assign Multiple]
```

### Counting Principles

1. **Independent Fixability Test (Primary Rule)**:
   - If flaw $A$ can be remediated without remediating flaw $B$, they MUST receive separate CVE IDs[^cve-program].
   - If remediating flaw $A$ intrinsically and necessarily remediates flaw $B$ because both stem from the exact same defect in code logic, exactly ONE CVE ID is assigned[^cve-program].
2. **Distinct Weakness Types (CWE Diversity)**:
   - If a module contains a Cross-Site Scripting (XSS) vulnerability (CWE-79) and a SQL Injection vulnerability (CWE-89) in the same endpoint, they must be assigned two distinct CVE IDs, even if discovered in the same audit, because their underlying weakness mechanisms and remediation logics are completely independent[^cve-program].
3. **Different Attack Vectors / Access Boundaries**:
   - Flaws exposed via unauthenticated remote networks versus authenticated local command-line interfaces generally represent distinct vulnerabilities requiring separate identifiers unless proven to share an identical defective parser or routine[^cve-program].
4. **Upstream Library vs. Downstream Product Rule**:
   - **Upstream Assignment**: A vulnerability identified in an upstream open-source library (e.g., OpenSSL, SQLite, or Apache Commons) receives exactly ONE authoritative CVE ID assigned by the upstream CNA or coordinator[^cve-program].
   - **Downstream Prohibition**: Downstream operating systems (e.g., Ubuntu, Debian, Red Hat), container images, or commercial appliances embedding that library MUST NOT assign downstream CVE IDs. Downstream distributors must track the vulnerability using the upstream CVE ID[^cve-program].
   - **Downstream Exception**: A downstream vendor may assign a separate CVE ID only if the vulnerability was introduced by the downstream vendor's custom modifications, patches, or integration glue logic[^cve-program].

# Scoping Determinations & Assignment Boundaries

CNAs must operate strictly within their formally registered scope:

- **First-Party Scopes**: A vendor CNA may only assign CVE IDs to products, firmware, and software for which it owns the source code or holds primary release responsibility[^cve-program].
- **Out-of-Scope Referrals**: If a researcher reports a vulnerability to a vendor CNA that affects a third-party commercial library or another vendor's product, the CNA must reject the assignment request and refer the finder to the appropriate vendor CNA, the governing Root CNA, or the Secretariat[^cve-program].
- **Coordinator Scopes**: Coordinator CNAs (e.g., CERT/CC, CISA, national CSIRTs) may assign CVE IDs to third-party software products whose vendors are not CNAs, provided coordinated disclosure protocols are followed[^iso-iec-29147].

# Practical Implementation & PSIRT Workflow

For a Product Security Incident Response Team (PSIRT) operating as a CNA:
1. **Intake Analysis**: When a report arrives, the triage team extracts all reported endpoints, vectors, and components.
2. **Root Cause Analysis (RCA)**: Development teams inspect the diffs. If fixing the issue requires modifying three separate repositories or implementing two distinct algorithmic patches, the PSIRT reserves two separate CVE IDs.
3. **Reservation via CVE Services API**: The PSIRT queries the CVE Services API:
   ```http
   POST /api/cve-id?cve_year=2026&amount=2&short_name=examplepsirt
   ```
   The API allocates the requested identifiers in the `RESERVED` state for internal tracking.

# Dates and Transitions

- **March 1, 2024**: CNA Rules v4.0 established the mandatory Independent Fixability standard and codified the strict prohibition against downstream duplicate CVE assignments for open-source library flaws.
- **CVE JSON 5.0 Requirement**: All assignments must link directly to structured version ranges under the `affected` array defined in Section 4.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 1: Program Overview](section-1-program-overview.md)
- [Section 2: Eligibility and Onboarding](section-2-eligibility-and-onboarding.md)
- [Section 4: Record Publishing](section-4-record-publishing.md)
- [Section 5: Embargo Management](section-5-embargo-management.md)
- [Section 6: Dispute Resolution](section-6-dispute-resolution.md)
- [CNA Container](../record-format/cna-container.md)
- [CWE Reference Data](../../../reference-data/cwe.md)
- [Triage and Validation Process](../../../process/triage-and-validation.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)
- [Finder Role](../../../roles/finder.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
