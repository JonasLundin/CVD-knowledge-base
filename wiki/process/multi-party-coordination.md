---
type: Procedure
title: 'Process: Multi-Party Vulnerability Coordination'
description: Procedures for managing vulnerabilities impacting shared libraries, protocols,
  or multi-vendor hardware components.
category: procedure
tags:
- cvd
- process
- multi-party
- cert-cc
- first
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: FIRST CVD Guide / ISO/IEC 29147 Clause 6
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Multi-Party Vulnerability Coordination** is the specialized coordination procedure required when a single vulnerability impacts multiple downstream vendors, an industry-wide protocol (e.g. TLS, BGP), a widely used open-source library (e.g. OpenSSL, Log4j), or common silicon hardware architecture (e.g. Spectre, Meltdown)[^iso-iec-29147].

# Coordination Architecture

```
                                  +------------------+
                                  | Finder / Reporter|
                                  +------------------+
                                           |
                                           v
                             +----------------------------+
                             |    Neutral Coordinator     |
                             | (CERT/CC, National CSIRT,  |
                             |   or OpenSSF Working Group)|
                             +----------------------------+
                                           |
                    +----------------------+----------------------+
                    |                      |                      |
                    v                      v                      v
             +--------------+       +--------------+       +--------------+
             | Vendor A     |       | Vendor B     |       | Vendor C     |
             | (OS Vendor)  |       | (Cloud Prov) |       | (Hardware)   |
             +--------------+       +--------------+       +--------------+
```

### Key Operational Challenges
- **Synchronized Disclosure Time (T-Zero)**: Agreeing on a single global release timestamp across international time zones to prevent premature disclosure.
- **Information Leaks**: Maintaining compartmentalized communication channels to avoid accidental leakages via public git commits or unencrypted trackers.
- **Shared Fix Collaboration**: Establishing private staging branches and shared testbeds for joint patch validation.

# Related concepts
- [Coordinator Role](../roles/coordinator.md)
- [Embargo Management and Coordination](embargo-management.md)
- [Advisory Publication and Patch Release](advisory-publication.md)

[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
