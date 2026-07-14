<div align="center">

# 🔦 Kashif · كاشف

**Client-side Secrets & Sensitive Data Exposure Scanner**

*Find the credentials you leaked — before someone else does.*

[![Live Tool](https://img.shields.io/badge/LIVE-siteq8.github.io%2FKashif-FFB454?style=for-the-badge)](https://siteq8.github.io/Kashif/)
![License](https://img.shields.io/badge/license-MIT-4BD6A0?style=for-the-badge)
![Privacy](https://img.shields.io/badge/telemetry-ZERO-FF5C5C?style=for-the-badge)

</div>

---

## Why Kashif exists

Every breach post-mortem has the same paragraph: *a credential was exposed in a repo, a log, a paste, a chat.* Secrets leak constantly — in commit diffs, CI logs, `.env` files, Slack exports, support tickets, even messages to AI assistants. Most people only find out after the crypto-miners do.

**Kashif** (Arabic: *revealer*) is a zero-install, zero-telemetry scanner you can hand to any developer, analyst, or auditor. Paste anything. Get an exposure report in seconds. **Nothing ever leaves the browser.**

## ✨ Features

| Capability | Detail |
|---|---|
| 🔑 **35+ signature patterns** | AWS, GitHub, GitLab, Anthropic, OpenAI, Stripe, Slack, Google, Azure, Twilio, SendGrid, npm, PyPI, Hugging Face, Telegram, Shopify, DigitalOcean, JWTs, private key blocks, DB connection strings, and more |
| 🧮 **Shannon entropy engine** | Catches *unknown* secret formats — high-entropy strings that look machine-generated |
| 💳 **Luhn validation** | Payment card detection with checksum verification (PCI DSS relevance flagged) |
| 🌍 **Gulf-region PII** | Kuwait & GCC IBAN detection, internal IP disclosure, email PII with GDPR/DPPR context |
| ✦ **AI triage (optional)** | Bring your own Anthropic API key — get blast-radius analysis and ordered rotation steps per finding. **Only masked values are sent, never the raw secret** |
| 📊 **Severity scoring** | CRITICAL → INFO with per-finding remediation guidance |
| 📄 **Export** | One-click Markdown or JSON exposure reports (all values masked) |
| 📁 **Multi-file** | Drag-and-drop entire config directories, logs, diffs |
| 🔒 **100% client-side** | Single HTML file. No backend. No analytics. Auditable in one read |

## 🚀 Use it

**Hosted:** https://siteq8.github.io/Kashif/

**Local / air-gapped:** download `index.html`, open it. That's it — works fully offline (fonts degrade gracefully).

```bash
git clone https://github.com/SiteQ8/Kashif.git && open Kashif/index.html
```

## 🧭 When to reach for it

- Pre-commit sanity check before pushing
- Reviewing a repo you inherited
- Auditing CI/CD logs and pipeline output
- Checking a chat/ticket/paste **before** sharing it
- Incident response: scoping what a leaked file actually contained
- Security awareness demos — the built-in **DEMO SAMPLE** is training-ready

## ⚠️ If Kashif finds a real secret

1. **Revoke first, investigate second.** Assume it was copied the moment it was exposed.
2. Rotate the credential and audit its usage logs (CloudTrail, GitHub security log, provider dashboards).
3. Purge it from git history (`git filter-repo` / BFG) — deleting the file is not enough.
4. Fix the root cause: secrets manager + pre-commit hooks + least-privilege scoped tokens with expiry.

## 🛡️ Privacy model

Scanning is pure in-browser JavaScript — **zero network calls**. The only optional network call is AI triage, which goes directly from *your* browser to `api.anthropic.com` using *your* key, carrying only the secret **type**, location, and a **masked** context line. Your key lives in page memory and is never persisted.

## 🤝 Contributing

New detection rules welcome — each rule is a single object (regex + severity + remediation). PRs to `RULES` in `index.html`.

---

<div align="center">

Built by **[Ali AlEnezi](https://3li.info)** · [@SiteQ8](https://github.com/SiteQ8) · Kuwait 🇰🇼

*Part of an open-source Gulf-region security tooling suite: [Marsad](https://github.com/SiteQ8) · Ghirbal · KWTWatch · Diwan*

</div>
