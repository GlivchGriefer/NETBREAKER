---
name: Documentation recommendation
about: Request clarifation / updated documentation
title: "[README]"
labels: documentation
assignees: GlivchGriefer

---

---
name: Documentation Request
about: Report unclear, missing, or incorrect documentation — including in-game walkthrough files
title: "[README] "
labels: documentation
assignees: ''
---

## What Documentation Is Affected?

Check all that apply:

- [ ] `README.md` — project overview, features, commands, shop table
- [ ] `CONTRIBUTING.md` — contribution guidelines or company schema
- [ ] `SECURITY.md` — security policy or reporting process
- [ ] `PATCH_vX.md` — patch notes for a specific version
- [ ] In-game `walkthrough.txt` — quick-start guide or topic index
- [ ] In-game `walkthrough-target-N.txt` — a specific target walkthrough
- [ ] In-game `walkthrough-web.txt` — web exploitation guide
- [ ] In-game `walkthrough-opsec.txt` — wanted system / evasion guide
- [ ] In-game `walkthrough-mining.txt` — mining and economy guide
- [ ] In-game `exploits.txt` — quick exploit reference
- [ ] In-game `tools.txt` — installed tools and commands
- [ ] In-game `man <command>` — a specific man page entry
- [ ] CVE-DB entry — description, exploit field, or remediation
- [ ] Other: ___

---

## Type of Issue

- [ ] **Incorrect** — something is factually wrong or describes the wrong behaviour
- [ ] **Missing** — a command, mechanic, or topic is undocumented
- [ ] **Unclear** — the explanation exists but is confusing or ambiguous
- [ ] **Outdated** — documentation describes behaviour from an older version
- [ ] **CompTIA alignment** — a concept maps incorrectly or incompletely to Security+ / PenTest+

---

## Describe the Problem

A clear description of what is wrong, missing, or confusing.

> Example: *`walkthrough-target-2.txt` says to run `privesc suid` after linPEAS, but the actual privesc path for NexGenPharm uses a SUID binary called `pharmactl` — the file doesn't mention the binary name, making the step hard to follow.*

Include the exact location if possible — file name, section heading, or command (`man exfil`, `cat walkthrough-opsec.txt`, etc.).

---

## Current Content

Paste or quote the current text that needs to change, if applicable.

```
Paste current text here
```

---

## Suggested Correction or Addition

What should it say instead, or what should be added?

```
Paste suggested text here
```

If you're not sure of the exact wording, describe what information is missing or what the correction should convey.

---

## NETBREAKER Version

In-game documentation lives inside the HTML file and is version-specific. Check the splash screen or boot message.

- Version: `v5.x`

---

## Additional Context

Any other context — related commands that are also undocumented, a CompTIA exam objective this maps to, or a link to the relevant official documentation.
