---
type: Rule
title: 'Section 6: Dispute Resolution and Appeals'
description: Escalation ladders, adjudication procedures, disputed record tagging, and formal appeal mechanisms under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-6-dispute-resolution
- appeals
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
  provision: Section 6
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 6: Dispute Resolution and Appeals** establishes the structured escalation process, adjudication standards, and arbitration mechanisms used to resolve disagreements arising within the CVE ecosystem[^cve-program]. As a decentralized, multi-stakeholder framework encompassing hundreds of commercial vendors, open-source projects, independent researchers, and sovereign coordinators, disagreements inevitably arise regarding vulnerability qualifications, counting decisions, scope boundaries, and record rejections[^iso-iec-30111].

Under CNA Operational Rules Version 4.0, Section 6 provides an objective, transparent, and binding appeal mechanism designed to uphold data integrity, prevent arbitrary record manipulation, and ensure fair treatment for all participants[^iso-iec-29147].

# Technical Scope & Dispute Typologies

Disputes handled under Section 6 typically fall into five primary categories:

1. **Vulnerability Qualification Disputes**: Disagreements between a researcher (finder) and a vendor CNA regarding whether a reported behavior constitutes a genuine security vulnerability or an intended design feature/operational misconfiguration[^cve-program].
2. **Assignment Scope Boundary Disputes**: Disagreements where a vendor CNA asserts that another CNA assigned a CVE ID for a product outside its designated scope, or where a third-party CNA assigned an ID to a first-party vendor's software without authorization[^cve-program].
3. **Counting and Splitting/Merging Disputes**: Controversies over whether a set of bugs should be tracked under a single aggregated CVE ID or split into multiple distinct identifiers under the independent fixability rule[^cve-program].
4. **Rejection and Invalidation Disputes**: Contested attempts by a CNA to transition a published CVE Record into the `REJECTED` state against the objections of finders or downstream consumers.
5. **Non-Responsive CNA Complaints**: Escalations initiated by researchers when a designated CNA fails to acknowledge or process vulnerability reports within mandatory operational timeframes[^cve-program].

# The Four-Tier Escalation Ladder

Section 6 codifies a formal, sequential escalation ladder that must be traversed when resolving technical or procedural disputes:

```
+-----------------------------------------------------------------+
| Tier 1: Direct Party-to-Party Negotiation                       |
|         Finder / Researcher <---> Designated CNA                |
|         Informal technical discussion, diff review, proof-of-concept |
+-------------------------------+---------------------------------+
                                |
                   (Unresolved after 30 days)
                                v
+-------------------------------+---------------------------------+
| Tier 2: Root CNA Adjudication                                   |
|         Governing Root CNA (e.g., CISA, ENISA, Red Hat Root)    |
|         Formal evidentiary review against CNA Rules v4.0        |
+-------------------------------+---------------------------------+
                                |
                     (Contested Determination)
                                v
+-------------------------------+---------------------------------+
| Tier 3: Top-Level Root / Secretariat Mediation                  |
|         TL-Root & CVE Secretariat (MITRE)                       |
|         Cross-root mediation, program-wide scope review         |
+-------------------------------+---------------------------------+
                                |
                     (Final Policy Deadlock)
                                v
+-------------------------------+---------------------------------+
| Tier 4: CVE Board Arbitration                                   |
|         CVE Board Quality Workgroup & Full Board Voting         |
|         Final, binding determination & official record decree   |
+-------------------------------+---------------------------------+
```

### Escalation Stages and Procedures

- **Tier 1 (Direct Engagement)**: Parties must attempt good-faith resolution directly. The complainant must provide reproducible proofs-of-concept (PoCs), environment specifications, and clear references to Section 3 counting rules[^iso-iec-29147].
- **Tier 2 (Root CNA Review)**: If unresolved after 30 calendar days, either party may escalate to the governing Root CNA. The Root conducts an objective technical review, examining source code diffs, security boundaries, and precedents. The Root issues a written determination directing assignment, splitting, or rejection[^cve-program].
- **Tier 3 (Secretariat Escalation)**: If a party contests the Root's finding, or if the dispute spans multiple Roots, the case is referred to the CVE Secretariat. The Secretariat verifies administrative compliance and technical alignment across program guidelines[^cve-program].
- **Tier 4 (CVE Board Final Appeal)**: In exceptional cases involving novel threat vectors, high-profile multi-stakeholder controversies, or fundamental policy interpretations, the CVE Board acts as the court of last resort. Board decisions are decided by formal vote and constitute final, binding authority[^cve-program].

# Handling Disputed Records (The `disputed` Tag)

When a technical disagreement regarding a vulnerability's validity cannot be definitively resolved because both parties present legitimate technical arguments, Section 6 prohibits unilateral suppression. Instead, the record is published with the formal **`disputed`** tag:

- **JSON 5.0 Schema Tag**: The CNA or Secretariat adds `"disputed"` to the `tags` array within the CVE Record:
  ```json
  "tags": ["disputed"]
  ```
- **Neutral Presentation of Evidence**: The record's description must objectively summarize both perspectives:
  > *"Acme Server 3.2 allows local users to overwrite configuration files via symlinks. The vendor disputes this report, asserting that write access to the affected directory requires root privileges, which already confers full system compromise under the vendor's published threat model."*
- **Consumer Empowerment**: This mechanism prevents arbitrary censorship while empowering enterprise risk managers to make informed, context-sensitive security decisions[^cve-program].

# Rejection and Retirement Workflows

When an assigned CVE ID is formally invalidated through dispute resolution (e.g., proven to be an unexploitable duplicate or retracted by the finder):
1. **Transition to REJECTED**: The CNA or Root transitions the record state to `REJECTED` via the CVE Services API (`PUT /api/cve/{cve_id}/cna`).
2. **Mandatory Justification**: The `rejectedReasons` array must document why the record was retired and reference any valid superseding CVE IDs:
   ```json
   "rejectedReasons": [
     {
       "lang": "en",
       "value": "This record was rejected as a duplicate of CVE-2026-99999. The underlying defect in the authentication parser was already tracked under the earlier identifier."
     }
   ]
   ```

# Dates and Transitions

- **March 1, 2024**: CNA Rules Version 4.0 codified the strict four-tier escalation hierarchy and standardized the format and requirements for `disputed` and `rejected` containers in CVE JSON 5.0.
- **Root Delegation**: The formal empowerment of continental Roots (such as ENISA in Europe) decentralized Tier 2 dispute handling.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 1: Program Overview](section-1-program-overview.md)
- [Section 3: CVE ID Assignment Rules](section-3-id-assignment-rules.md)
- [Section 4: Record Publishing](section-4-record-publishing.md)
- [Section 5: Embargo Management](section-5-embargo-management.md)
- [Rejected Container](../record-format/rejected-container.md)
- [Secretariat Role](../../../roles/secretariat.md)
- [Coordinator Role](../../../roles/coordinator.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)
- [Finder Role](../../../roles/finder.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
