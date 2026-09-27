---
type: Concept
title: CVE Root Hierarchy and Delegation Model
description: Governance structure connecting the Secretariat, Top-Level Roots, and
  Roots to individual CNAs across industry domains.
category: programme
tags:
- cvd
- programmes
- cve
- roots
- cnas
- hierarchy
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: ISO/IEC 29147:2018 Information technology - Security techniques - Vulnerability
    disclosure
  author: International Organization for Standardization
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: binding
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CVE Program** employs a distributed hierarchical delegation model ensuring scalable governance of hundreds of CNAs worldwide[^iso-iec-29147].

# Structural Tiers
1. **CVE Secretariat**: Operates root administrative services, program policies, and primary registry backups (MITRE).
2. **Top-Level Roots (TLRs)**: Entities with broad domain oversight (e.g., CISA for US ICS/OT; ENISA/CISA cooperation).
3. **Roots**: Manage specific clusters of CNAs (e.g., Red Hat Root for Open Source, Siemens Root for Industrial).
4. **CNAs**: Vendor and researcher organizations authorized to assign CVE IDs to vulnerabilities within their scope.

# Related concepts
- [Roots and CNAs Index](index.md)
- [CNA Role](../../../roles/cna.md)

[^iso-iec-29147]: International Organization for Standardization, ISO/IEC 29147:2018 Information technology - Security techniques - Vulnerability disclosure, https://www.iso.org/standard/72311.html
