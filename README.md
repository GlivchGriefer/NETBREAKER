```
███╗   ██╗███████╗████████╗██████╗ ██████╗ ███████╗ █████╗ ██╗  ██╗███████╗██████╗
████╗  ██║██╔════╝╚══██╔══╝██╔══██╗██╔══██╗██╔════╝██╔══██╗██║ ██╔╝██╔════╝██╔══██╗
██╔██╗ ██║█████╗     ██║   ██████╔╝██████╔╝█████╗  ███████║█████╔╝ █████╗  ██████╔╝
██║╚██╗██║██╔══╝     ██║   ██╔══██╗██╔══██╗██╔══╝  ██╔══██║██╔═██╗ ██╔══╝  ██╔══██╗
██║ ╚████║███████╗   ██║   ██████╔╝██║  ██║███████╗██║  ██║██║  ██╗███████╗██║  ██║
╚═╝  ╚═══╝╚══════╝   ╚═╝   ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝
```

# **Penetration Testing Simulator**
![Version](https://img.shields.io/github/v/tag/GlivchGriefer/NETBREAKER?label=version&style=flat-square&color=00ff41)
### **All targets, companies, IPs and exploits are entirely fictional.**
#### **Educational simulation based on CompTIA Security+ / PenTest+ methodology.**

---

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=flat-square&logo=gnu&logoColor=white)
![Single File](https://img.shields.io/badge/delivery-single%20HTML%20file-00ff41?style=flat-square)
![No Dependencies](https://img.shields.io/badge/dependencies-none-00ff41?style=flat-square)

---

## Overview

NETBREAKER is a single-file, browser-based cybersecurity simulation game. Players work through a fictional darknet as a penetration tester, discovering targets, running recon, exploiting vulnerabilities, escalating privileges, and exfiltrating data — all using commands modelled on real-world tools and CompTIA Security+ / PenTest+ methodology.

No installation. No server. No dependencies beyond a modern browser. Open the HTML file and play.

---

## Educational Context

NETBREAKER is designed as an interactive reference for the CompTIA Security+ and PenTest+ certification tracks. Every command, technique, and CVE in the game maps to a real concept:

- **Recon phase** — passive (sniffer) vs. active (nmap, gobuster) information gathering, OSINT
- **Exploitation** — CVE research, service fingerprinting, authenticated vs. unauthenticated attack paths
- **Web application testing** — OWASP Top 10 categories: SQLi, XSS, IDOR, LFI, CSRF, auth bypass
- **Post-exploitation** — privilege escalation vectors (sudo, SUID, cron, token impersonation), persistence, lateral movement, data exfiltration
- **OPSEC** — log clearing, IP rotation, covert channels (DNS exfil), detection evasion

---

## Features

### Terminal Emulator

A full in-browser terminal with command history (arrow keys), tab-autocomplete, a scrollable output buffer, and a persistent prompt that reflects your current session context (`handle@nb:~$` locally, `user@domain:/path$` on a target).

Every command has a manual page accessible via `man <command>`. Type `help` for a categorised command reference with the full attack chain at the top.

### Five Panes

| Pane | Function |
|------|----------|
| **TERM** | Primary terminal — all commands run here |
| **BROWSER** | In-game web browser with form interaction, vulnerability indicators, and browser tools |
| **FILES** | Interactive filesystem explorer for local virtual files and connected target filesystems |
| **NET** | SVG force-directed network map showing all targets, their status, and relationships |
| **CVE-DB** | Searchable vulnerability database that grows as you discover CVEs via nmap |

### Browser Pane Tools

- **INTERCEPT** — Burp Suite–style request capture. Pause any HTTP request, edit headers and body, then forward, drop, or send modified.
- **cURL Builder** — Construct custom HTTP requests with method, headers, and body. Detects SQLi, LFI, and auth bypass patterns in responses.
- **FUZZER** — Automatically tests all input fields on the current page for SQLi, XSS, LFI, and IDOR.
- **COOKIES** — Inspect and modify session cookies and role tokens.
- **DIFF** — Side-by-side baseline vs. modified response comparison to confirm exploit success.

### Network Map

Force-directed SVG graph rendered with a custom physics simulation (repulsion, spring forces, center pull). Nodes are sized by target difficulty and coloured by compromise status — undiscovered, discovered, shell, rooted. Hosts running miners display an amber ring. Hover for a tooltip; click to open the target modal with attack suggestions and contract status.

### CVE Database

Nine base entries covering the core fictional CVEs used in the game. Running `nmap -sV -sC` on targets dynamically discovers up to ten additional entries (including simulated versions of Baron Samedit, PwnKit, Dirty Pipe, Shellshock, BlueKeep, and others). Newly found CVEs are badged **NEW** in the database and immediately usable with `exploit`.

### Economy and Progression

Credits are earned through gameplay — not handed to the player at start. Every meaningful action pays out:

| Action | Reward |
|--------|--------|
| Scan discovers a host | +10c per host |
| nmap finds a CVE | +15c per vulnerability |
| gobuster run | +20c |
| Sniffer deployed | +30c |
| Web or SSH login | +40–50c |
| Exploit — shell | +75c |
| Root shell | +150c |
| Privilege escalation | +100c |
| Contracts | +200c to +30,000c |
| Mining (per 30s tick) | +8c to +80c per rig |

REP unlocks harder targets. Credits unlock tools. Mining provides compound passive income as you root more hosts.

### Mining System

Deploy an XMR miner on any rooted host with `deploy miner <ip>`. Income is credited every 30 seconds. Rates scale with target difficulty (easy=8c, med=18c, hard=35c, elite=80c per tick). Buying the Mining Pool from the shop doubles all rates. The topbar shows live income rate and the `miners` command lists all active rigs.

### OPSEC and Wanted System

A 0–5 star wanted level rises with noisy actions (exploiting IDS-protected targets, brute force, HTTP exfil). At three stars, an IDS alert bar appears. Tools and commands to manage heat:

- `clearlogs` — wipe local traces, −1 wanted (free)
- `clearlogs <ip>` — wipe remote logs, −2 wanted (requires Log Cleaner tool)
- `rotateip` — rotate attacker IP, break active traces, −2 wanted (requires IP Rotator)
- **VPN Chain** — passive, reduces wanted gain rate by 60%
- **TOR Router** — passive, prevents wanted gain entirely; required for elite targets

### Virtual File System

Local virtual files accessible via `cat` or the FILES pane at any time, no connection required:

| File | Contents |
|------|----------|
| `walkthrough.txt` | Quick-start guide and topic index |
| `walkthrough-targets.txt` | Full walkthroughs for all 7 targets |
| `walkthrough-web.txt` | SQLi, XSS, IDOR, LFI, CSRF technique guide |
| `walkthrough-opsec.txt` | Wanted system, log clearing, evasion |
| `walkthrough-mining.txt` | Mining setup, rates, economy progression |
| `exploits.txt` | Quick exploit reference |
| `tools.txt` | Installed tools and their commands |

### Script Editor

`editor` opens a script editor with four built-in templates (port scanner, privilege check, DNS exfil, reverse shell). Scripts are saved per-operative and executable with `run <name>`. Target filesystem scripts (e.g. `/opt/scripts/monitor.sh`) can also be executed with `run` when connected and in the correct directory.

### Procedural Company Schema

All seven targets are defined as plain JavaScript objects in the `COMPANY_DEFS` array. The game engine reads every field uniformly — nothing is hardcoded to a specific company. To add a custom target, append a new object following the schema documented in the source:

```js
// Fields: id, name, domain, ip, industry, desc,
//   diff (easy/med/hard/elite), repReq (int),
//   sec { fw, ids, mfa, waf } (bool),
//   scanReq { nmap, gobuster, sniffer } (bool),
//   ports [{ num, svc, ver, vuln, note }],
//   creds { user: pass },
//   rootMethod (str),
//   webVulns [str], webPages [str],
//   fs { path: [entries] }, fc { path: content },
//   contracts [{ id, title, desc, target, reward: { c, r } }]
```

### Save System

Three save slots backed by IndexedDB. Saves auto-persist every 15 seconds and on session close. Each slot shows handle, credit balance, REP, and last-saved date on the title screen.

---

## Targets

| # | Company | IP | Difficulty | REP Required |
|---|---------|-----|-----------|--------------|
| 1 | PetroFlow Systems | 192.168.10.14 | Easy | 0 |
| 2 | NexGenPharm Research | 10.0.5.22 | Medium | 200 |
| 3 | Darkpeak Analytics | 10.20.5.50 | Medium | 500 |
| 4 | Arclight Financial Group | 172.16.5.100 | Hard | 600 |
| 5 | OmniCloud Hosting | 185.14.6.88 | Hard | 1,000 |
| 6 | CivicGrid Power Authority | 10.10.1.5 | Elite | 1,800 |
| 7 | Sentinel Defense Systems | 172.31.10.5 | Elite | 3,500 |

All companies, IP addresses, domain names, personnel, CVE identifiers, and exploits are entirely fictional and created for educational simulation purposes.

---

## Commands

Commands support piping: `cd /var/www/html | ls` executes each segment in sequence.
Tab-autocomplete and command history (↑/↓) available in the terminal at all times.

```
RECON
  scan <subnet>                    Ping sweep. Discovers live hosts. (+10c/host, one-time)
  nmap [flags] <ip>                Port, service, and CVE scan. Populates CVE-DB.
    -sV (versions)  -sC (scripts)  -O (OS)  -p- (all ports)  -A (aggressive)
  gobuster <ip>                    Web directory brute-force. (+20c, one-time per target)
  deploy sniffer <ip>              Passive credential capture. Silent — no IDS trigger. (+30c)
  deploy crawler <ip>              Web content and link mapping.
  agents                           View results from all deployed sniffers and crawlers.
  ping <ip>                        Test reachability. (+5c per unique source→destination pair)

EXPLOITATION
  exploit <vuln> <ip>              Run exploit module. Requires metasploit for CVE exploits.
    exploit CVE-2017-7679 <ip>     Apache mod_mime RCE
    exploit CVE-2020-1938 <ip>     Ghostcat AJP file read
    exploit CVE-2022-1388 <ip>     F5 BIG-IP auth bypass
    exploit vsftpd-backdoor <ip>   Instant root bind shell
    exploit S7-auth-bypass <ip>    Siemens ICS (metasploit-pro)
    exploit sqli / xss / lfi / csrf / idor <ip>   Web app exploits
  brute <svc> <ip>                 Credential brute-force. Noisy — triggers IDS.
    services: ssh  ftp  mysql  http-form
  nc [-lvnp <port>] [<ip> <port>]  Netcat. Bind shells, reverse shells.
  curl <url> [-X method] [-d body] [-H header]   Manual HTTP request.

ACCESS
  ssh [user@]<ip>                  SSH login. (+50c first login per target)
  ftp <ip>                         FTP connection and version fingerprint.
  su [user]                        Switch user on connected target.
  sudo <cmd>                       Run as root — reveals NOPASSWD privesc path if available.
  disconnect / exit / q            Close current target session.

FILESYSTEM
  ls [path]                        List directory. Works locally and on connected target.
  cd <path>                        Change directory. Works locally and on connected target.
  cat <file>                       Read file. Also reads local virtual files.
  pwd                              Print working directory.
  find [-name <pattern>]           Search filesystem on connected target.
  grep [-r] [-i] [-n] <pat> [file] Search file contents on connected target.
  chmod / touch / mkdir            Simulated filesystem operations on target.
  run <name>                       Execute a saved editor script or target filesystem script.
                                   Accepts name with or without .sh extension.

POST-EXPLOITATION
  privesc [method]                 Escalate privileges. (+100c escalation, +150c root shell)
    linpeas    Auto-scan for sudo / SUID / cron vectors (recommended first)
    sudo       NOPASSWD sudo to /bin/bash
    suid       SUID binary exploitation
    cron       Writable cron job injection
    token      Windows SeImpersonatePrivilege → SYSTEM (metasploit-pro)
    mimikatz   Windows LSASS credential dump (mimikatz tool)
    hmi-admin  ICS HMI admin panel → root (CivicGrid)
  persist <method>                 Install persistence. Requires root.
    cron  backdoor  service
  exfil <path> [method]            Exfiltrate file and complete matching contracts.
    https (default, low noise)  dns (covert, needs exfil-kit)  http (noisy)
  pivot <src> <dst>                Lateral movement through compromised host. (metasploit-pro)

OPSEC
  clearlogs [ip]                   Wipe logs. Local: −1 wanted. Remote: −2 wanted.
  rotateip                         Rotate attacker IP via proxy chain. −2 wanted.

MINING
  deploy miner <ip>                Deploy XMR miner on rooted host. Passive income every 30s.
  miners                           List all active rigs and total income rate.

SYSTEM / ENVIRONMENT
  whoami / id                      Current user, UID, groups, session info, credits.
  uname [-a]                       OS and kernel info. Context-aware: local or target.
  ps                               Running processes on connected target.
  hostname [name]                  Print or set attacker machine hostname. Persists in save.
  ifconfig                         Network interface info. Works locally and on target.
  ip a / ip route                  IP addresses and routing table.
  env                              Environment variables for current session.
  history                          Last 20 commands from session history.
  echo <text>                      Print text to terminal.
  which <cmd>                      Locate a command binary.

INFORMATION
  cve [term]                       Search CVE-DB. `cve discovered` = only nmap-found CVEs.
  man <cmd>                        Detailed manual page for any command (29 entries).
  help                             Full categorised command reference with attack chain.

OTHER
  contracts                        List active and completed contracts with rewards.
  shop                             Open darknet tool shop.
  editor                           Script editor with 4 templates. Run with: run <name>
  clear                            Clear terminal output.
```
---

## Shop — Tools

| Tool | Category | Cost | Effect |
|------|----------|------|--------|
| netcat | Network | Free | TCP/UDP connections, bind shells |
| nmap advanced | Recon | Free | OS detection, scripting engine |
| gobuster | Recon | 100c | Web directory brute-force |
| hydra | Exploit | 150c | Network login brute-forcer |
| sqlmap | Web | 200c | SQL injection automation |
| Metasploit | Exploit | 300c + 50 REP | CVE exploitation framework |
| linPEAS | Post | 400c + 80 REP | Linux privilege escalation scanner |
| Burp Suite | Web | 800c + 150 REP | Web proxy (INTERCEPT pane) |
| Log Cleaner | OPSEC | 800c | Remote log wipe, −2 wanted |
| Persistence Kit | Persist | 700c + 120 REP | Cron, backdoor, service |
| Exfil Toolkit | Exfil | 900c + 180 REP | Covert DNS/HTTPS channels |
| IP Rotator | OPSEC | 1500c + 150 REP | Rotate IP, break traces |
| VPN Chain | OPSEC | 1200c + 200 REP | Passive −60% wanted gain |
| mimikatz | Post | 1800c + 300 REP | Windows LSASS credential dump |
| Metasploit Pro | Exploit | 2500c + 400 REP | Token impersonation, pivoting |
| XMR Miner | Mining | 500c + 50 REP | Passive income on rooted hosts |
| Mining Pool | Mining | 2000c + 200 REP | Doubles all miner rates |
| TOR Router | OPSEC | 3500c + 700 REP | No wanted gain, elite unlock |

---
## Known Issues

---
## Patch Log

### v5.3 — Theme, Map, and Walkthrough Overhaul
- Light theme now correctly swaps background (#f0f4f0) and text (#1a2a1a) — all base CSS
  elements use `var(--bg)` and `var(--textd)` so the toggle affects every pane
- Network map uses `ResizeObserver` and absolute SVG positioning to fill the full pane
  at any screen size; re-renders automatically on window resize
- `walkthrough-targets.txt` removed; replaced by 7 individual files
  (`walkthrough-target-1.txt` through `walkthrough-target-7.txt`), each gated behind
  target discovery — locked targets return a REP requirement message
- `walkthrough.txt` index updated to list per-target files with difficulty and REP
- Version strings updated to 5.3 in splash screen and boot message

### v5.2 — Terminal Authenticity and UX Fixes
- nmap reward fixed — guard now ensures reconDone is initialised before flag check
- IDOR discovery awards +15c per unique user ID retrieved without auth
- Multiple toasts now stagger vertically instead of stacking on top of each other
- Terminal tab relabelled TERMINAL with `>_` icon
- `hostname [name]` command lets the user set their attacker machine hostname; persists in save
- Exfil folder in FILES pane now expands to list exfiltrated files on click
- `ls` and `cd` work on the local (attacker) machine when not connected to a target
- Suggested attack sequence removed from network map target modal
- Network map now uses viewBox scaling to fill 100% of the pane at any screen size
- `walkthrough-targets.txt` split into per-target files (`walkthrough-target-1.txt` through `walkthrough-target-7.txt`); each file only reveals targets already discovered
- New authentic Linux commands: `grep [-r -i -n]`, `find [-name]`, `id`, `uname [-a]`, `ps`, `history`, `echo`, `ifconfig`, `ip a / ip route`, `env`, `sudo`, `su`, `chmod`, `touch`, `mkdir`, `which`
- Tab autocomplete covers all new commands

### v5.1 — Economy Hardening

- All recon bonuses (scan, nmap, gobuster, sniffer) are now strictly one-time per target and persist across saves — credits can no longer be farmed by repeating recon commands
- Re-running a rewarded recon action prints `[*] Already rewarded — no bonus.` so the player understands why no credits were awarded
- Ping bonus (+5c) tracks unique source→destination pairs and persists in save state

### v5.0 — Polish and Economy Fixes
- SSH login bonus (+50c) now awarded once per target; re-awarded separately on first web portal login (+40c)
- Contract completion box is now fixed-width with all text centered and equal-length top/bottom borders
- `ping` awards +5c per unique source→destination pair; local-to-target and target-to-target pings tracked separately
- `ping` latency is now context-aware: local-to-remote shows realistic WAN latency (~8–40ms), target-to-target shows LAN latency (~0.1–3ms)
- Network map now fills the full pane height, scrollable on small screens, and scales node spacing and repulsion force with the number of entries

### v4.1 — Bug Fix
- Fixed `run <script>` not resolving target filesystem scripts; `run monitor.sh` now executes scripts found in the current working directory on a connected target
- Fixed `cat <script>.sh` showing `[Binary or unreadable file]` for target shell scripts; now displays content with a read-only notice
- `run` now accepts names with or without `.sh` extension

### v4.0 — Full Rebuild
- Complete file rewritten from scratch via Python string writes to eliminate all heredoc escaping and Cloudflare injection issues
- Procedural company schema: all 7 targets defined as plain JS objects in `COMPANY_DEFS`; custom companies can be appended following the documented schema
- Split walkthrough files: `walkthrough.txt` is now an index; topic files cover targets, web, opsec, and mining separately
- `help` command reorganised with attack chain summary at top and full categorised reference below
- `man` pages added for every command (25+ entries); tab-autocomplete covers all commands
- Dynamic CVE discovery: `nmap -sV -sC` adds up to 10 new entries to CVE-DB with **NEW** badge; `cve discovered` lists only found CVEs
- SVG force-directed network map replaces ASCII; custom physics simulation with repulsion, spring forces, and center pull; node colour/size reflects status and difficulty; mining ring indicator; hover tooltips; click opens target modal
- `run` command now checks target filesystem in addition to local editor scripts

### v3.0 — Feature Expansion
- Added 3 new targets: Darkpeak Analytics (med), OmniCloud Hosting (hard), Sentinel Defense Systems (elite) — total 7 targets
- Mining system: `deploy miner <ip>` on rooted hosts earns passive credits every 30s; rates scale with difficulty; Mining Pool doubles all rates; live income shown in topbar
- OPSEC commands: `clearlogs [ip]` wipes logs and reduces wanted; `rotateip` breaks active traces
- Credit rewards added to all major actions: scan, nmap, gobuster, sniffer, login, exploit, root, privesc
- Credits start at 0; early game balanced so first target is reachable through recon rewards alone
- Tool costs rebalanced: Metasploit 300c, gobuster 100c, sqlmap 200c
- `exit` and `q` added as aliases for `disconnect`

### v2.0 — Core Rewrite
- Rebuilt as single clean HTML file written via Python to avoid Cloudflare script-tag injection and email obfuscation
- All inline `onclick` handlers removed; events attached exclusively via `addEventListener` in `DOMContentLoaded` — eliminated phantom modal bug
- IndexedDB save system with 3 operative slots and auto-save every 15 seconds
- Wanted system (0–5 stars) with decay over time and IDS alert bar at 3 stars
- Browser pane with INTERCEPT, cURL builder, FUZZER, COOKIES, DIFF tools
- Web vulnerability simulation: SQLi login bypass, IDOR on `/api/users`, stored XSS in contact forms, LFI indicators, CSRF indicators
- Five panes: Terminal, Browser, Files, Network, CVE-DB
- Script editor with four built-in templates

### v1.0 — Initial Release
- Single-file browser game with in-terminal command interface
- Four fictional targets: PetroFlow, NexGenPharm, Arclight Financial, CivicGrid Power
- Core commands: scan, nmap, gobuster, deploy, exploit, privesc, persist, exfil, ssh, ftp, nc, contracts, shop
- CVE database with 9 base entries
- ASCII network map
- IndexedDB persistence
- CompTIA Security+ / PenTest+ methodology throughout

---

## License

```
NETBREAKER — Penetration Testing Simulation
Copyright (C) 2026

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <https://www.gnu.org/licenses/>.
```

All fictional companies, IP addresses, domain names, personnel, CVE identifiers, and exploit descriptions in this software are created for educational simulation purposes only. They bear no relation to any real organisation, network, system, or vulnerability. This software is not intended to facilitate or instruct real-world attacks on any system.
