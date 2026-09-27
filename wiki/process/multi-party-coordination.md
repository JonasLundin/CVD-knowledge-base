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
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: FIRST CVD Guide / ISO/IEC 29147 Clause 6
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Multi-Party Vulnerability Coordination** is the specialized coordination procedure required when a single vulnerability impacts multiple downstream vendors, an industry-wide protocol (e.g. TLS, BGP), a widely used open-source library (e.g. OpenSSL, Log4j), or common silicon hardware architecture (e.g. Spectre, Meltdown).

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

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
