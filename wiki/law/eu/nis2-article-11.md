---
type: Law
title: 'NIS2 Directive Article 11: Coordinated Vulnerability Disclosure & European
  Vulnerability Database'
description: Statutory framework mandating Member States to establish national CVD
  frameworks, designate CSIRT coordinators, and establishing the EUVD under ENISA.
category: law
tags:
- cvd
- law
- nis2
- directive-eu-2022-2555
- euvd
- csirt-coordinator
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: nis2-directive
  resource: http://data.europa.eu/eli/dir/2022/2555/oj
  title: Directive (EU) 2022/2555 on measures for a high common level of cybersecurity
    across the Union (NIS2)
  author: European Parliament and Council of the European Union
  last_modified: '2022-12-14T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: binding
  instrument_status: in_force
  provision: Directive (EU) 2022/2555 Article 11
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Article 11 of Directive (EU) 2022/2555 (NIS2)** establishes the European Union's foundational legal architecture for **Coordinated Vulnerability Disclosure (CVD)** and mandates the creation of the **European Vulnerability Database (EUVD)**[^nis2-directive].

Article 11 removes the historical legal ambiguity surrounding security research across EU Member States, transforming CVD from an informal industry practice into a mandatory, institutionalized public policy.

# Statutory Structure of Article 11

```
+-------------------------------------------------------------------+
|               NIS2 ARTICLE 11 STATUTORY ARCHITECTURE              |
+-------------------------------------------------------------------+
| Paragraph 1: NATIONAL CVD FRAMEWORKS & CSIRT COORDINATORS         |
| - Member States must adopt national CVD policies                  |
| - Designate one CSIRT as coordinator for multi-party / disputes   |
+-------------------------------------------------------------------+
| Paragraph 2: THE EUROPEAN VULNERABILITY DATABASE (EUVD)           |
| - ENISA develops and maintains Union-wide database                |
| - Publicly accessible, machine-readable, vendor-neutral           |
+-------------------------------------------------------------------+
| Paragraph 3: CSIRT COORDINATOR POWERS & OBLIGATIONS               |
| - Act as trusted intermediary between finders and vendors         |
| - Identify and contact affected entities                          |
| - Assist researchers in negotiations and legal safe-harbor        |
| - Facilitate embargo timeline management                          |
+-------------------------------------------------------------------+
| Paragraph 4: COOPERATION WITH THE CSIRTS NETWORK                  |
| - Cross-border coordination of vulnerabilities impacting multiple |
|   Member States or critical infrastructure sectors                |
+-------------------------------------------------------------------+
```

# Operational Mandates for Member States & CSIRTs

1. **Designated CSIRT Coordinators (Article 11(1))**:
   - Each Member State must designate one of its CSIRTs as a **trusted coordinator**.
   - The designated CSIRT acts as an intermediary where the finder cannot reach the vendor or where the vendor fails to acknowledge or remediate the vulnerability.
2. **Support for Security Researchers**:
   - CSIRTs must provide clear, secure intake mechanisms for vulnerability reporters.
   - Promote safe-harbor protections to shield good-faith researchers from criminal prosecution or civil litigation.
3. **The European Vulnerability Database (EUVD) (Article 11(2))**:
   - ENISA operates the EUVD in consultation with the CSIRTs Network.
   - Publishes verified vulnerability descriptions, affected ICT products/services, severity ratings (CVSS), and links to vendor patches.
   - Operates as a CVE Top-Level Root for European Union bodies and agencies.

# Related concepts
- [European Vulnerability Database (EUVD)](../../programmes/euvd.md)
- [Coordinator Role](../../roles/coordinator.md)
- [Multi-Party Vulnerability Coordination](../../process/multi-party-coordination.md)
- [CRA Vulnerability Handling Provisions](cra-vulnerability-handling.md)

[^nis2-directive]: European Parliament and Council of the European Union, Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2), http://data.europa.eu/eli/dir/2022/2555/oj
