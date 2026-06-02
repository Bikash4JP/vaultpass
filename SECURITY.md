# Security Policy

VaultPass takes security vulnerabilities seriously. This document explains how to report security issues and what to expect from us in response.

## 🛡️ Our Commitment

- **Acknowledge** reports within **48 hours**
- **Validate and triage** within **7 days**
- **Provide a fix timeline** based on severity (see below)
- **Publish a post-mortem** for any confirmed vulnerability
- **Credit reporters** in our Hall of Fame (with permission)
- **No legal action** against good-faith security researchers

## 🚨 Reporting a Vulnerability

**Please do NOT open a public GitHub issue for security vulnerabilities.** Public disclosure before a patch is available puts users at risk.

### Preferred channels

1. **GitHub Private Vulnerability Reporting** — [report here](https://github.com/Bikash4JP/vaultpass/security/advisories/new) *(preferred)*
2. **Email** — `security@vaultpass.io` *(once domain is configured)*
3. **Direct contact** — [@Bikash4JP](https://github.com/Bikash4JP) via GitHub

### What to include

- Description of the vulnerability and its impact
- Steps to reproduce, including code or proof-of-concept if possible
- Affected versions, platforms, or components
- Any suggested mitigations (optional)
- Your name and contact info (for credit — say if you wish to remain anonymous)

## 🎯 Scope

### In scope

- Zero-knowledge guarantee violations
- Authentication bypass or session hijacking
- Encryption weaknesses (IV reuse, weak key derivation, algorithm downgrade)
- Authorization failures (accessing another user's vault data)
- Refresh token attacks (replay, reuse after rotation, forgery)
- Client-side secret exposure (keys leaking to storage, logs, or network)
- Server-side data leakage (metadata exposure, log file contents)

### Out of scope

- DoS attacks against the free hosted service
- Social engineering of VaultPass team members
- Physical attacks against user devices
- Vulnerabilities in third-party dependencies (report to upstream first)
- Issues requiring physical access to an unlocked device

## ⚡ Severity & Response SLA

| Severity | Definition | Response SLA |
|---|---|---|
| 🔴 **CRITICAL** | Zero-knowledge guarantee broken. Active exploitation possible. | Patch within **24 hours**. Emergency release. |
| 🟠 **HIGH** | Authentication bypass or cross-user data access possible. | Patch within **7 days**. Coordinated disclosure. |
| 🟡 **MEDIUM** | Security degraded but zero-knowledge maintained. Exploitation requires user action. | Patch within **30 days**. Next release cycle. |
| 🟢 **LOW** | Defense-in-depth weakened. No direct user impact. | Patch within **90 days**. Standard PR process. |

## 🤝 Disclosure Process

VaultPass follows **coordinated disclosure**:

1. Reporter submits via private channel
2. VaultPass acknowledges within 48 hours
3. Severity is jointly assessed; fix timeline agreed
4. Fix is developed in a private `security/*` branch
5. Patch is released with a [GitHub Security Advisory](https://github.com/Bikash4JP/vaultpass/security/advisories)
6. Full post-mortem published within 14 days of patch release
7. Reporter is credited (with permission) in the Hall of Fame

## 🏆 Hall of Fame

We publicly thank security researchers who have helped us improve VaultPass. *(This list will grow as the project matures.)*

---

*Last updated: 2025*