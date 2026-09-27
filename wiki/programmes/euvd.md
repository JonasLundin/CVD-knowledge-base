---
type: Programme
title: European Vulnerability Database (EUVD)
description: Union-wide database maintained by ENISA pursuant to Article 11 of NIS2
  collecting, cataloging, and publishing ICT vulnerabilities.
category: programme
tags:
- cvd
- programme
- euvd
- enisa
- nis2
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
  authority_level: rule
  instrument_status: in_force
  provision: NIS2 Directive Article 11(2)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **European Vulnerability Database (EUVD)** is the Union-wide, publicly accessible vulnerability database developed and operated by the European Union Agency for Cybersecurity (**ENISA**) pursuant to **Article 11(2) of Directive (EU) 2022/2555 (NIS2)**[^nis2-directive].

EUVD serves as a central European repository for publicly known vulnerabilities in ICT products and services, ensuring non-discriminatory access and providing machine-readable advisories to all European organizations and CSIRTs.

# Legal Mandate & Core Functions

Under NIS2 Article 11:
1. **Repository Operations**: ENISA must establish and maintain the European vulnerability database in consultation with the CSIRTs Network.
2. **Harmonized Metadata**: The database must provide transparent description of the vulnerability, affected ICT products or services, severity, and availability of patches.
3. **Automated Interoperability**: EUVD interfaces with national CSIRT repositories, vendor CSAF feeds, and international registries (CVE Program, NVD).
4. **CNA / Root Status**: ENISA functions as a CVE Top-Level Root for European Union bodies and Member State authorities.

# Related concepts
- [The CVE Program](cve-program.md)
- [NIS2 Article 11: Coordinated Vulnerability Disclosure](../law/nis2-article-11.md)
- [CSAF 2.0 Security Advisory Profile](../formats/csaf/csaf-security-advisory.md)

[^nis2-directive]: European Parliament and Council of the European Union, Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2), http://data.europa.eu/eli/dir/2022/2555/oj
