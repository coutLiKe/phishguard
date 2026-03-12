# 🎣 PhishGuard — Phishing URL Detector

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![No Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen?style=for-the-badge)
![Privacy First](https://img.shields.io/badge/Privacy-100%25%20Local-blue?style=for-the-badge)

> A browser-based phishing URL analyzer that detects suspicious patterns used by real-world attackers — no backend, no tracking, no dependencies.

---

## 🖥️ Live Demo

**[▶ Open Live Demo](https://yourusername.github.io/phishguard)**

Or open `index.html` directly in any browser. No install, no server needed.

---

## ✨ Features

- **17 detection checks** covering documented real-world attacker techniques
- **Risk score (0–100)** with a clear verdict: Safe / Suspicious / High Risk
- **Colored URL breakdown** — visually dissects protocol, subdomain, domain, TLD, path, and parameters
- **Per-signal explanations** — every flag explains *why* it's suspicious in plain English
- **Threat category badges** — Brand Spoof, Raw IP, Open Redirect, Typosquat, and more
- **URL statistics** — total length, subdomain depth, parameter count, path depth
- **Light / Dark mode toggle** — preference saved across sessions via localStorage
- **5 built-in example URLs** covering the most common attack types
- **100% private** — zero network requests, all logic runs in the browser

---

## 🧠 Detection Methods

| # | Check | What it detects |
|---|-------|----------------|
| 1 | Protocol | HTTP vs HTTPS — unencrypted pages |
| 2 | IP Address | Raw IP used instead of a domain name |
| 3 | URL Shortener | bit.ly, tinyurl.com, etc. hiding the real destination |
| 4 | Risky TLD | Free/abused TLDs: .tk, .ml, .xyz, .top, and others |
| 5 | Brand Impersonation | Known brand names embedded in fake domains |
| 6 | Homoglyph / Typosquat | paypa**1**.com, **0**utlook.com — digit-for-letter swaps |
| 7 | Subdomain Depth | paypal.com.evil-domain.tk trick |
| 8 | Brand-in-Subdomain | paypal.evil.tk — real domain is evil.tk |
| 9 | @ Symbol Abuse | https://google.com@evil.com |
| 10 | Double Slash Redirect | //evil.com embedded in path |
| 11 | Open Redirect Parameters | ?redirect=, ?url=, ?next= patterns |
| 12 | Suspicious Path Keywords | /login, /verify, /suspended, /confirm |
| 13 | Excessive URL Length | > 150 characters |
| 14 | Encoded Payload Parameters | Long Base64-like query strings |
| 15 | Executable Extensions | .exe, .zip, .bat, .php in path |
| 16 | Homoglyph Normalization | Normalizes 0→o, 1→l, 3→e before brand matching |
| 17 | HTTPS Misuse Warning | Clarifies that HTTPS ≠ safe |

---

## 🔍 Built-in Example URLs

Try these in the app to see detections in action:

```
# Paypal homoglyph + suspicious keywords
http://paypa1-secure.login-verify.com/account?suspended=true

# Brand-in-subdomain trick + risky TLD
https://secure-bankofamerica.com.phish.tk/login

# URL shortener hiding the real destination
https://bit.ly/3xK9mZp

# Raw IP address + open redirect parameter
http://192.168.1.1/admin/login.php?redirect=http://evil.com
```

---

## 📂 Project Structure

```
phishguard/
├── index.html     ← Full app (HTML + CSS + JS, single file)
├── README.md      ← This file
├── LICENSE        ← MIT license
└── .gitignore     ← Ignores OS/editor clutter
```

---

## 🚀 Deployment (GitHub Pages)

1. Create a new public GitHub repo named **`phishguard`**
2. Upload all files
3. Go to **Settings → Pages → Branch: main / root → Save**
4. Live at `https://yourusername.github.io/phishguard` in ~60 seconds

---

## 🔒 Privacy

- Zero network requests after page load (except Google Fonts)
- No analytics, no cookies, no data stored server-side
- URLs never leave your device
- Theme preference saved locally via `localStorage`

---

## ⚠️ Limitations

This tool performs **static structural analysis** — it analyzes the shape and patterns of a URL, not the live page content. It will not catch:

- Newly registered domains with no suspicious patterns yet
- Compromised legitimate websites
- Phishing pages hosted on trusted platforms (e.g. Google Forms, SharePoint)

For production environments, combine with threat intelligence feeds such as the VirusTotal API, Google Safe Browsing, or PhishTank.

---

## 🗺️ Potential Improvements

- [ ] VirusTotal API integration (using URL hashing to preserve privacy)
- [ ] WHOIS lookup for domain age — newly registered domains are a strong phishing signal
- [ ] PhishTank database check
- [ ] Export scan report as PDF
- [ ] Browser extension version for inline checking before clicking

---

## 📄 License

MIT — free to use, modify, and distribute.

---

*Part of a defensive security portfolio. Companion project: [PassGuard](https://github.com/yourusername/passguard) — Password Security Analyzer.*
