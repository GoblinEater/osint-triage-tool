# OSINT Triage Tool

**Version:** 2.0  
**Part of:** [Goblin Eaters Cyber Cavern](https://ubritsa.com)

A browser-based, single-file OSINT triage tool for analysts. Paste an artifact, get instant links to the right investigation services. No installation, no account required, no data leaves your machine except when you click a service link.

---

## What It Does

Takes an indicator of compromise (IOC) or other artifact and routes it to the appropriate OSINT lookup services automatically — no need to remember which tool handles which artifact type.

Supports two modes:

**Single Artifact** — paste one item, the tool detects its type and presents a curated set of relevant services with pre-populated links.

**Bulk Extract** — paste any block of raw text (log file, email body, report, raw headers) and the tool automatically extracts all recognizable artifacts and queues them for triage.

---

## Supported Artifact Types

| Type | Examples | Detection Method |
|---|---|---|
| IP Address | `198.51.100.42` | IPv4 regex |
| Email Address | `user@example.com` | RFC-style regex |
| Domain | `example.com` | TLD pattern match |
| URL | `https://example.com/path` | Protocol prefix |
| File Hash | MD5, SHA-1, SHA-256 | Hex length (32/40/64) |
| Phone Number | `+1-919-555-0100` | NANP-style pattern |
| Email Header | Raw header block | Presence of `Received:`, `DKIM-Signature:`, `Message-ID:` |

---

## Services by Artifact Type

### IP Address
- **ip2location** — Geolocation, ISP, proxy/VPN detection
- **AbuseIPDB** — Community abuse reports and confidence score
- **Shodan** — Open ports, services, banners, CVEs
- **VirusTotal** — 70+ vendor reputation check
- **Talos Intelligence** — Cisco threat intel and reputation
- **ARIN Whois** — ASN, netblock, and org ownership
- **whois.com** — Registration and abuse contact info
- **CentralOps** — DNS, traceroute, service scan
- **MXToolbox Blacklist** — RBL/spam list check

### Email Address
- **Have I Been Pwned** — Known breach and paste exposure
- **ThatsThem** — Reverse email lookup (names, phones, addresses)
- **VirusTotal** — Domain reputation check
- **MXToolbox Email Health** — MX, SPF, DKIM, DMARC
- **whois.com** — Domain registration info
- **Talos Intelligence** — Domain reputation
- **CentralOps** — Full domain dossier

### Domain
- **VirusTotal** — Multi-vendor reputation
- **Shodan** — Infrastructure exposure
- **Talos Intelligence** — Reputation and sender score
- **whois.com** — Registrar, registrant, nameservers
- **ARIN Whois** — IP block and ASN
- **MXToolbox Email Health** — Mail server health
- **CentralOps** — DNS, traceroute, service scan
- **ip2location** — Resolve to IP and check geolocation

### URL
- **VirusTotal** — URL reputation scan
- **urlscan.io** — Screenshot and behavioral analysis
- **URLVoid** — Blacklist and reputation check
- **Talos Intelligence** — Domain reputation of the URL host

### File Hash (MD5 / SHA-1 / SHA-256)
- **VirusTotal** — Multi-vendor malware scan
- **MalwareBazaar** — Malware sample database
- **Hybrid Analysis** — Sandbox behavioral report

### Phone Number
- **ThatsThem** — Reverse phone lookup
- **NumVerify** — Line type and carrier info

### Email Header
- **MXToolbox Header Analyzer** — Visual header trace and hop analysis
- **Google Admin Toolbox** — SPF/DKIM/DMARC pass/fail per hop

---

## Export / Triage Notes

Single artifact mode includes an **Export triage note** button that generates a Markdown-formatted analyst note with the artifact, type, timestamp, and pre-populated service links. Bulk mode includes **Export all as markdown** for a full triage report across all extracted artifacts.

Both exports copy to clipboard for pasting into ticketing systems, case notes, or reports.

---

## Privacy

All detection and classification runs locally in your browser. No artifact data is transmitted anywhere unless you click a service link — at which point only the data needed for that specific lookup is sent to that service.

---

## Usage

Open `osint-triage-tool.html` in any modern browser. No server, no build step, no dependencies.

---

## Part of the Goblin Eaters Cyber Cavern Toolset

- [OSI Attack Explainer](https://ubritsa.com/tools/osi-attack-explainer.html)
- [IPv4 vs IPv6 Security Posture Visualizer](https://ubritsa.com/tools/ipv4_v_ipv6_heel_analysis.html)
