---
name: Tell me if it's wrong
about: If you find something invalid or hindering learning, use this
title: "[WRONG]"
labels: invalid
assignees: GlivchGriefer

---

---
name: Educational Concern
about: Report content that is inaccurate, misleading, or counterproductive to learning
title: "[WRONG] "
labels: educational-concern
assignees: ''
---

## What Content Is Affected?

Check all that apply:

- [ ] In-game `walkthrough-target-N.txt` — target attack path or technique description
- [ ] In-game `walkthrough-web.txt` — web exploitation concepts
- [ ] In-game `walkthrough-opsec.txt` — OPSEC or evasion concepts
- [ ] In-game `walkthrough-mining.txt` — economy or mining description
- [ ] In-game `man <command>` — a man page entry
- [ ] CVE-DB entry — description, phase, or remediation guidance
- [ ] Terminal command output — misleading or incorrect feedback
- [ ] `README.md` — feature description or educational context section
- [ ] `CONTRIBUTING.md` — CompTIA alignment table
- [ ] Other: ___

---

## Type of Concern

- [ ] **Technically inaccurate** — a concept, technique, or term is described incorrectly
- [ ] **CompTIA misalignment** — a mechanic or description maps incorrectly to Security+ / PenTest+ objectives
- [ ] **Misleading simplification** — the game simplifies a concept in a way that builds bad habits or wrong mental models
- [ ] **Missing context** — a technique is demonstrated without explaining the defensive countermeasure or real-world consequence
- [ ] **Outdated** — the description reflects deprecated tooling, old CVE information, or obsolete methodology
- [ ] **Terminology** — incorrect or inconsistent use of industry-standard terms
- [ ] **Other**: ___

---

## Describe the Concern

A clear description of what is inaccurate, misleading, or missing, and why it matters for learning.

> Example: *The `walkthrough-opsec.txt` file says TOR prevents all wanted gain, which teaches players that TOR makes operations fully untraceable. In reality TOR reduces but does not eliminate forensic exposure — the game mechanic is fine, but the framing should note this is a simplification.*

---

## Location

Where exactly does the content appear? Include the file name, command, or section.

> Example: `cat walkthrough-opsec.txt` → section "PASSIVE PROTECTION"
> Example: `man exfil` → DNS exfil description
> Example: CVE-DB entry `CVE-2020-1938` → exploit field

---

## Current Content

Paste the current text that needs to change.

```
Paste current content here
```

---

## Suggested Correction

What should it say instead? If you are unsure of exact wording, describe what the correction should convey.

```
Paste suggested correction here
```

**Reference (optional):** Link to a CompTIA exam objective, NIST publication, OWASP entry, or other authoritative source that supports the correction.

---

## Impact on Learning

How does the current content hinder or mislead someone studying for Security+ / PenTest+, or learning penetration testing methodology?

> Example: *A student who internalises "TOR = untraceable" may make poor OPSEC decisions in a professional engagement and misanswer related exam questions about anonymisation limitations.*

---

## NETBREAKER Version

- Version: `v5.x`

---

## Additional Context

Any other context, related content that has the same issue, or suggestions for how the game mechanic and the real-world concept could be better reconciled.
