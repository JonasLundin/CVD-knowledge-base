---
type: Programme
title: European Vulnerability Database (EUVD)
description: Public European repository of known ICT vulnerabilities maintained by ENISA under NIS2 Article 12(2), operating as a CVE Root.
category: programme
tags:
- programme
- euvd
- enisa
- nis2
- cve-root
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: eu-nis2-directive
  resource: http://data.europa.eu/eli/dir/2022/2555/oj
  title: Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2)
  author: European Parliament and Council of the European Union
  last_modified: '2022-12-14T00:00:00Z'
- id: enisa-euvd
  resource: https://euvd.enisa.europa.eu
  title: European Vulnerability Database Portal
  author: European Union Agency for Cybersecurity (ENISA)
  last_modified: '2025-05-13T00:00:00Z'
x-cvd:
  jurisdiction: EU
  authority_level: statutory
  instrument_status: in_force
  provision: Directive (EU) 2022/2555 Article 12(2)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **European Vulnerability Database (EUVD)** is the European Union's authoritative platform for cataloging, disclosing, and distributing information on vulnerabilities in ICT products and services, developed and managed by ENISA pursuant to Article 12(2) of the NIS2 Directive[^eu-nis2-directive][^enisa-euvd].

# Institutional Governance and CVE Root Status

## ENISA CVE Root Status
On **November 20, 2025**, ENISA was formally designated as a **CVE Root** within the CVE Program hierarchy (reporting to Top-Level Roots). In this capacity, ENISA oversees and accredits European National CSIRTs and regional organizations operating as Candidate or operational CVE Numbering Authorities (CNAs).

## Integration with the CSIRTs Network
The EUVD operates in close operational coordination with the EU CSIRTs Network, providing:
1. Cross-border vulnerability coordination workflows.
2. Automated ingest and distribution of CSAF 2.0 advisories and VEX documents.
3. Alignment with CVSS 4.0 and SSVC scoring taxonomies.

# Related concepts
- [NIS2 Article 12](../law/eu/nis2-article-12.md)
- [Root Hierarchy and Delegation](cve/roots-and-cnas/root-hierarchy-and-delegation.md)
- [CSAF Formats](../formats/csaf/index.md)

[^eu-nis2-directive]: European Parliament and Council of the European Union, Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2), http://data.europa.eu/eli/dir/2022/2555/oj
[^enisa-euvd]: European Union Agency for Cybersecurity (ENISA), European Vulnerability Database Portal, https://euvd.enisa.europa.eu
