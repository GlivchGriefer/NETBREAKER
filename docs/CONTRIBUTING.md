```
███╗   ██╗███████╗████████╗██████╗ ██████╗ ███████╗ █████╗ ██╗  ██╗███████╗██████╗
████╗  ██║██╔════╝╚══██╔══╝██╔══██╗██╔══██╗██╔════╝██╔══██╗██║ ██╔╝██╔════╝██╔══██╗
██╔██╗ ██║█████╗     ██║   ██████╔╝██████╔╝█████╗  ███████║█████╔╝ █████╗  ██████╔╝
██║╚██╗██║██╔══╝     ██║   ██╔══██╗██╔══██╗██╔══╝  ██╔══██║██╔═██╗ ██╔══╝  ██╔══██╗
██║ ╚████║███████╗   ██║   ██████╔╝██║  ██║███████╗██║  ██║██║  ██╗███████╗██║  ██║
╚═╝  ╚═══╝╚══════╝   ╚═╝   ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝
```

# Contributing to NETBREAKER

Thanks for your interest in contributing. NETBREAKER is a single-file educational cybersecurity simulation. All targets, companies, CVEs, and exploits are entirely fictional and designed to map to CompTIA Security+ / PenTest+ methodology.

---

## Ground Rules

### What this project is

A browser-based game for learning penetration testing concepts — recon, exploitation, privilege escalation, exfiltration, OPSEC — in a safe, fictional environment. Every mechanic exists to teach a real concept through gameplay rather than passive reading.

### What this project is not

A toolkit, a framework, or a reference for attacking real systems. Contributions that blur this line will not be accepted regardless of how they are framed.

### Non-negotiable constraints

- All targets, IPs, domain names, company names, CVE identifiers, and personnel are **fictional**. Do not base them on real organisations, real vulnerabilities with working exploit code, or real people.
- Exploit implementations are **simulated outcomes** — shell obtained, file read, credential captured — not functional attack code. A contribution must not contain code that would work outside the game's fictional context.
- The game must remain a **single HTML file** with no external dependencies beyond Google Fonts (already loaded). No npm, no build step, no CDN beyond that.

---

## Ways to Contribute

### Adding a custom target company

The most common and encouraged contribution. The company schema is fully procedural — append an object to `COMPANY_DEFS` in the source and the engine reads it uniformly.

**Minimum required fields:**

```js
{
  id: 'c7',                        // unique, sequential
  name: 'Fictional Corp Name',
  domain: 'fictional-domain.tld',
  ip: '10.x.x.x',                  // RFC 1918 or fictional range only
  industry: 'Sector description',
  desc: 'One-line description for the network map card.',
  diff: 'easy|med|hard|elite',
  repReq: 0,                        // REP gate to unlock
  sec: { fw: false, ids: false, mfa: false, waf: false },
  scanReq: { nmap: false, gobuster: false, sniffer: false },
  ports: [
    { num: 22, svc: 'SSH', ver: 'OpenSSH 8.x', vuln: 'CVE-ID-or-NB-ID', note: 'Brief note' }
  ],
  creds: { 'username': 'password' },
  rootMethod: 'Description of privesc path',
  webVulns: ['sqli', 'xss'],        // subset of: sqli sqli-blind xss idor lfi csrf auth-bypass
  webPages: ['home', 'portal'],
  fs: { '/': ['etc','home'], '/etc': ['passwd'] },
  fc: { '/etc/passwd': 'root:x:0:0...' },
  contracts: [
    { id: 'xx-c1', title: 'Contract Name', desc: 'Brief description.',
      target: '/path/to/flag.txt', reward: { c: 800, r: 150 } }
  ]
}
```

**Checklist before submitting a target PR:**

- [ ] All names, IPs, and domains are entirely fictional with no resemblance to real organisations
- [ ] CVE IDs reference entries already in `CVE_DB` or `CVE_DISCOVERED`, or include a new `NB-XXX-XXX` entry
- [ ] The `rootMethod` describes the path in plain English — no functional exploit code
- [ ] `fc` file contents are plausible config files, logs, and notes — no real credentials, no real sensitive data even as examples
- [ ] Difficulty and REP gate are consistent with existing targets (see table in README)
- [ ] At least two contracts with meaningful rewards
- [ ] Tested in browser — `cat walkthrough-target-N.txt` displays correctly after discovery

---

### Adding CVE entries

New CVE entries fall into two categories:

**`CVE_DB` (base, always visible):** General reference entries covering categories relevant to the game's attack surface. Should map to a technique a player encounters, not be a random entry.

**`CVE_DISCOVERED` (unlocked via nmap):** Entries that appear in the database only after a player scans a target that exposes them. Must have a corresponding `CVE_DISC_MAP` entry linking a `vuln` string on a port to the CVE ID.

**Entry format:**

```js
{
  id: 'CVE-YYYY-NNNNN',          // or NB-PREFIX-NNN for fictional
  name: 'Short descriptive name',
  score: 9.8,                    // CVSS v3 base score
  sev: 'critical|high|med',
  service: 'Service Name version',
  port: 443,
  desc: 'One paragraph. Must include [FICTIONAL SIM] prefix for NB- entries.',
  exploit: 'Terminal commands showing how to trigger it in-game.',
  fix: 'Remediation guidance.',
  phase: 'Recon|Exploitation|Privilege Escalation|Pivot|Web Exploitation'
}
```

Real CVE entries should reflect documented public knowledge — CVSS score, affected service, and remediation. The exploit field describes the **in-game command** only, not functional attack code.

---

### UI and terminal improvements

Good contributions in this area:

- New authentic Linux commands (`awk`, `sed`, `diff`, `tar`, `wget`, `crontab -l`, etc.) that respond contextually to whether you're on the attacker machine or a connected target
- Browser pane improvements — additional web vulnerability simulations, better INTERCEPT UX
- Network map visual improvements — new node states, better tooltips, accessibility
- Theme refinements — additional CSS variable coverage, high-contrast mode
- Mobile / touch UX improvements

The terminal should feel like a real shell. Commands should behave consistently with their real counterparts for flags and output format, except where the game mechanic requires a fictional outcome.

---

### Documentation

- Corrections to walkthrough files (`VFILES` in source) — accuracy, clarity, CompTIA alignment
- README improvements
- Additional man page entries for commands that lack them

---

## Code Style

NETBREAKER is intentionally a single file. Keep it that way.

- **No external dependencies.** Everything runs from the one HTML file.
- **Vanilla JS only.** No frameworks, no transpilers.
- **`var` throughout** — the codebase uses ES5-style declarations for consistency. Don't introduce `let`/`const` unless you're refactoring a whole section.
- **No inline event handlers.** All events via `addEventListener` in `DOMContentLoaded`. This is enforced — inline handlers caused the phantom modal bug in v1 and we are not going back.
- **No email addresses in strings.** Cloudflare mangles them. Use `[at]` notation in display text.
- **No `<script>` tags inside JS strings.** Use `'\u003c'+'script\u003e'` or the `SCRTAG` constant.
- **Write data via Python, not heredoc** if generating the file programmatically. Shell heredoc truncates and mangles apostrophes.
- **Syntax check before PR:** Extract the JS block and run `node --check` on it. PRs that break the syntax check will be closed without review.

```bash
# Quick syntax check
python3 -c "
with open('netbreaker-vX.X.html') as f:
    c = f.read()
js = c[c.index('<script>')+8:c.rindex('</script>')]
open('/tmp/nb_check.js','w').write(js)
"
node --check /tmp/nb_check.js
```

---

## Pull Request Process

1. Fork the repository and create a branch named `feature/description` or `fix/description`.
2. Make your changes to the single HTML file.
3. Run the syntax check above.
4. Open a PR with:
   - A summary of what changed and why
   - Which patch note category it falls under (new target / CVE / UI / terminal / docs)
   - Confirmation that all fictional content checks pass
5. PRs that introduce real exploit code, real organisation names, or external dependencies will be closed.

---

## Reporting Issues

Open a GitHub issue with:

- **Version** — visible on the splash screen and in the boot message
- **Browser and OS**
- **Steps to reproduce**
- **Expected vs actual behaviour**
- **Console errors** if applicable (F12 → Console)

For gameplay bugs (wrong credit award, broken command, save corruption), include your operative's current REP and credits if relevant.

---

## Educational Scope

NETBREAKER maps to the following CompTIA domains. Contributions should align with at least one:

| Domain | Coverage in game |
|--------|-----------------|
| Reconnaissance | `scan`, `nmap`, `gobuster`, `deploy sniffer` |
| Scanning & Enumeration | Port profiles, service versions, CVE discovery |
| Exploitation | `exploit`, `brute`, web vulnerability browser tools |
| Post-Exploitation | `privesc`, `persist`, `exfil`, `pivot` |
| Web Application Testing | OWASP Top 10 simulations in browser pane |
| OPSEC / Evasion | Wanted system, `clearlogs`, `rotateip`, TOR, VPN Chain |
| Reporting | Contracts, exfil log, CVE-DB entries |

---

## Disclaimer

All fictional companies, IP addresses, domain names, personnel, CVE identifiers, and exploit descriptions in NETBREAKER are created for educational simulation purposes only. They bear no relation to any real organisation, network, system, or vulnerability. This project is not intended to facilitate or instruct real-world attacks on any system.

By contributing, you agree that your contribution upholds this intent.

---

*Licensed under the GNU General Public License v3.0*
