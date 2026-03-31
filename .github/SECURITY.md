# Security Policy

## Scope

NETBREAKER is a single-file, client-side browser application with no server, no backend, and no network communication beyond loading Google Fonts. All gameplay data is stored locally in the browser's IndexedDB.

Security issues relevant to this project are those that could affect **users of the game** — for example, XSS in rendered content, save data corruption or exfiltration, or malicious content injected via the fictional web browser pane.

This project does not accept reports about the fictional exploit simulations, fictional CVEs, or fictional attack commands inside the game. Those are intentional educational mechanics, not vulnerabilities.

---

## Supported Versions

Only the current release receives security updates. Given the single-file delivery model, updates are straightforward to apply — download the latest file and replace the previous one.

| Version | Supported          |
|---------|--------------------|
| 5.4.x   | :white_check_mark: |
| 5.3.x   | :x:                |
| 5.2.x   | :x:                |
| 5.1.x   | :x:                |
| < 5.0   | :x:                |

---

## What Counts as a Vulnerability

### In scope

- **XSS via user-controlled input** — the operator callsign, hostname field, script editor, or any in-game form field that renders output back to the DOM without sanitisation
- **Save data exfiltration** — any path by which IndexedDB save data could be read by a third-party script or exfiltrated without user interaction
- **Malicious content injection** — any way a crafted save file or URL could execute arbitrary code when the file is opened in a browser
- **Cloudflare injection surface** — the file is served through Claude.ai's Cloudflare proxy; any pattern in the source that causes Cloudflare to inject or rewrite content in a way that creates a code execution path
- **Theme or localStorage abuse** — `localStorage` is used for theme preference only; any path that allows that surface to be abused

### Out of scope

- The fictional exploit commands (`exploit`, `nmap`, `brute`, etc.) — these are game mechanics that print simulated output, not functional attack code
- The fictional CVE database entries — these are educational descriptions, not working exploits
- The in-game INTERCEPT / cURL / FUZZER browser tools — these simulate HTTP concepts against fictional in-memory targets only; no real HTTP requests are made
- Bugs that require the user to deliberately modify their own save file via browser dev tools
- Issues in Google Fonts or other third-party resources loaded at runtime
- Theoretical attacks requiring physical access to the user's device

---

## Reporting a Vulnerability

Please **do not** open a public GitHub issue for security vulnerabilities. Opening a public issue before a fix is available gives no benefit and could expose other users.

**To report a vulnerability:**

1. Open a [GitHub Security Advisory](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing/privately-reporting-a-security-vulnerability) on this repository using the private disclosure path (Security → Report a vulnerability).
2. Include:
   - A clear description of the issue
   - The version of the file affected (visible on the splash screen)
   - The browser and OS where you reproduced it
   - Steps to reproduce, including any crafted input or save data
   - Your assessment of impact and exploitability

**What to expect:**

| Timeline | Action |
|----------|--------|
| Within 48 hours | Acknowledgement that the report was received |
| Within 7 days | Initial assessment — confirmed, declined, or needs more information |
| Within 30 days | Fix released for confirmed vulnerabilities, or a documented decision not to fix with rationale |

If a vulnerability is **confirmed**, you will be credited in the patch notes unless you request otherwise.

If a vulnerability is **declined** (out of scope, not reproducible, or working as intended), you will receive an explanation.

---

## Expectations for Researchers

- Test only against your own local copy of the file
- Do not attempt to access, modify, or exfiltrate another user's save data
- Do not submit reports generated entirely by automated scanners without manual verification — the fictional CVE and exploit content in the source will produce false positives at scale
- Coordinate disclosure timing before publishing a writeup

---

## Notes on the Single-File Architecture

Because NETBREAKER ships as a single HTML file with all JS inline:

- There are no npm dependencies and no `package.json` — dependency vulnerability scanners will find nothing to scan, which is expected
- The only external resource loaded at runtime is Google Fonts over HTTPS — if you are auditing in an offline environment, this request will fail silently and the fallback monospace font will be used
- All data is stored in the browser's IndexedDB under the key `netbreaker_db` — no cookies, no `sessionStorage` beyond theme preference in `localStorage`
- The Cloudflare proxy on Claude.ai rewrites `<script>` tags and email addresses in served HTML — the source is written to avoid these patterns; if you find one that slipped through, that is a valid report

---

*This policy applies to the NETBREAKER game source. All fictional companies, IPs, CVEs, and exploit descriptions in the game are educational simulations with no relation to real systems or organisations.*
