<div align="center">

# 🔐 VaultPass

### Zero-Knowledge Password Manager

**We don't know your passwords. That's the point.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-0d9e7a.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Status](https://img.shields.io/badge/Status-Pre--Alpha-orange.svg)]()
[![Platforms](https://img.shields.io/badge/Platforms-iOS_·_Android_·_Web-0a192f.svg)]()

</div>

---

## What is VaultPass?

VaultPass is an open-source, end-to-end encrypted password manager for iOS, Android, and web. The defining principle: **the server stores only ciphertext**. Even if our database is fully compromised — breached, subpoenaed, or inspected by the developer — no attacker can read a single password, because encryption and decryption happen exclusively on the user's device.

This is enforced by **architecture**, not by policy.

## Why VaultPass exists

In 2022, LastPass was breached. 25 million encrypted vaults were stolen. Since then, over $35 million in cryptocurrency has been drained from users whose vaults were eventually cracked offline.

In February 2026, peer-reviewed research exposed **25 distinct attack vectors** across Bitwarden, LastPass, Dashlane, and 1Password — directly challenging their zero-knowledge claims.

The market needs a password manager that:

- Cannot leak what it does not know
- Is open-source so the claims can be verified, not just trusted
- Treats Asia-Pacific users — especially Japan — as first-class citizens, not an afterthought
- Is mobile-first, not a desktop app with a mobile port

## Core principles

| | |
|---|---|
| 🔒 **Zero-knowledge by architecture** | The server is mathematically incapable of reading vault contents |
| 🌐 **Open source** | AGPL-3.0 licensed. All code public. All security claims verifiable |
| 📱 **Mobile-first** | Built with React Native from day one |
| 🇯🇵 **Bilingual** | English and Japanese, first-class support |
| 🛡️ **Security as foundation** | Not a feature. Not a marketing claim. The base layer |

## Status

🚧 **Pre-Alpha — Under active development.**

VaultPass is being built in public. See [`/docs`](./docs) for the founding document set and roadmap, and the [GitHub Project board](https://github.com/Bikash4JP/vaultpass/projects) for live progress.

## Documentation

| Document | Description |
|---|---|
| [Company Charter](./docs/01-company-charter.md) | Mission, vision, core values |
| [Product Vision](./docs/02-product-vision.md) | Target audience, positioning, market |
| [Engineering Principles](./docs/03-engineering-principles.md) | Non-negotiable rules, code standards |
| [Contributing Guide](./CONTRIBUTING.md) | Git workflow, PR process, commit standards |
| [Security Policy](./SECURITY.md) | Vulnerability disclosure |
| [Roadmap](./docs/06-roadmap.md) | Milestones M0 → v1.0 |
| [Governance](./docs/07-governance.md) | Open-source model |

## License

VaultPass is licensed under the **GNU Affero General Public License v3.0** (AGPL-3.0).

This means: anyone can use, modify, and self-host VaultPass. Any modifications offered as a network service must also be released under AGPL-3.0. See [LICENSE](./LICENSE) for full terms.

## Contact

- **Security vulnerabilities:** see [SECURITY.md](./SECURITY.md)
- **General questions:** open a [GitHub Discussion](https://github.com/Bikash4JP/vaultpass/discussions)
- **Maintainer:** [@Bikash4JP](https://github.com/Bikash4JP)

---

<div align="center">
<sub>Built with care in Yokohama, Japan · 横浜から世界へ</sub>
</div>