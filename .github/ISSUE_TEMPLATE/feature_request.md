---
name: Feature request
about: Pitch your idea for the project
title: "[REQUEST]"
labels: enhancement
assignees: GlivchGriefer

---

---
name: Feature Request
about: Suggest a new feature or improvement for NETBREAKER
title: "[REQUEST] "
labels: enhancement
assignees: ''
---

## Is Your Feature Request Related to a Problem?

A clear and concise description of the frustration or gap this addresses.

> Example: *I'm always frustrated that after rooting a target I have to remember the exact exfil path — there's no way to quickly see what files are available without switching to the Files pane.*

---

## Feature Category

Check the most relevant category:

- [ ] New target company
- [ ] New command or terminal behaviour
- [ ] New Linux-authentic command
- [ ] Browser pane tool (INTERCEPT / FUZZER / cURL / COOKIES / DIFF)
- [ ] Network map improvement
- [ ] CVE database entry or discovery mechanic
- [ ] Economy / credit / contract system
- [ ] Mining system
- [ ] OPSEC / wanted system
- [ ] Save system / operative management
- [ ] UI / theme / accessibility
- [ ] Documentation / walkthrough content
- [ ] New shop tool
- [ ] Other: ___

---

## Describe the Solution You'd Like

A clear and concise description of what you want to happen.

> Example: *After rooting a target, a `loot` command that lists all readable files in the target's `fc` object — similar to running `find / -readable` — so the player can see what's available to exfil without navigating the filesystem manually.*

If relevant, describe how it would integrate with existing commands, the economy, or the progression system.

---

## Educational Alignment

NETBREAKER maps to CompTIA Security+ / PenTest+ methodology. How does this feature support learning?

> Example: *`loot` teaches post-exploitation enumeration — a key phase in the PenTest+ exam that covers identifying high-value data after gaining access.*

If the feature is purely quality-of-life rather than educational, that's fine too — just note it here.

---

## Fictional Content Checklist

If your request involves new targets, CVEs, companies, or exploit scenarios:

- [ ] All company names, IPs, domains, and personnel are entirely fictional
- [ ] No real organisations, real CVEs with working exploit code, or real people are referenced
- [ ] Exploit outcomes are simulated (shell obtained, file read) — not functional attack code

---

## Describe Alternatives You've Considered

Any alternative approaches, workarounds, or related commands that partially address the need.

> Example: *The Files pane does show the filesystem, and `ls` / `cat` work on the target. But switching panes breaks terminal flow. A terminal-side summary would keep operators in context.*

---

## Single-File Constraint

NETBREAKER ships as one HTML file with no build step or external dependencies. Does your feature fit within this constraint?

- [ ] Yes — pure HTML / CSS / vanilla JS
- [ ] Needs discussion — describe below

If you have a rough idea of how it could be implemented within the single-file architecture, include it here.

---

## Mockup or Example Output

If applicable, show what the feature might look like — example terminal output, UI sketch, or command syntax.

```
$ loot

[POST-EXPLOITATION LOOT — petroflow.local]

  Credentials found:
    /home/backup/creds.bak       marcus.reed / Pipeline2019!
    /var/www/html/config.php     db root / root

  Key files:
    /root/flag.txt               [contract target]
    /home/marcus.reed/notes.txt
    /home/marcus.reed/.bash_history

  Scripts:
    /opt/scripts/monitor.sh
    /home/backup/backup.sh       [runs as root via cron]

  Run: exfil <path> https   to extract any file above
```

---

## Additional Context

Any other context, screenshots, references to similar tools, or CompTIA exam topics this relates to.
