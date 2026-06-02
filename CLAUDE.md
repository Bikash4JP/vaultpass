# VaultPass — Claude Code Project Context

> **Read this file first.** It defines who we are, how we work, and what's non-negotiable. Every Claude Code session loads this automatically.

---

## What is VaultPass?

VaultPass is a **zero-knowledge, end-to-end encrypted password manager** for iOS, Android, and web. The defining principle: **the server stores only ciphertext**. Encryption and decryption happen exclusively on the user's device. Even a full server breach exposes zero user data.

This is enforced by **architecture**, not by policy.

---

## Project status

- **Stage:** M0 — Foundation (initial scaffolding)
- **Default branch:** `develop`
- **Production branch:** `main` (protected — never push directly)
- **License:** AGPL-3.0
- **Public repository:** github.com/Bikash4JP/vaultpass

---

## Founding documents

Before making architectural decisions, read these in `/docs/`:

- `01-company-charter.md` — Mission, vision, core values
- `02-product-vision.md` — Target audience, positioning, market analysis
- `03-engineering-principles.md` — Non-negotiable engineering rules
- `04-contributing.md` — Git workflow and PR process (also `CONTRIBUTING.md`)
- `05-security-policy.md` — Vulnerability disclosure (also `SECURITY.md`)
- `06-roadmap.md` — Milestones M0 → v1.0
- `07-governance.md` — Open-source governance model

---

## Non-negotiable engineering rules

These are **constraints**, not guidelines. Violation = PR rejection. No exceptions.

1. **Never transmit the master password or encryption key to any server.**
2. **Never store sensitive data in AsyncStorage, localStorage, or plaintext files.** Use `expo-secure-store` (mobile) or memory-only (web).
3. **Never use `Math.random()` for cryptographic operations.** Use `crypto.getRandomValues()` or platform-native CSPRNG.
4. **Never reuse an IV in AES-GCM.** Generate a fresh 96-bit IV per encryption.
5. **Never store plaintext credentials in any database field.** Server stores ciphertext only.
6. **Never merge to `main` without passing tests and code review.**
7. **Never hardcode secrets, API keys, or credentials in source code.** Use `.env` (gitignored), `.env.example` (committed template).
8. **Never add a dependency without a documented justification** in `DEPENDENCY.md`.

---

## Code quality standards

- **Language:** TypeScript strict mode everywhere. No `any`, no `@ts-ignore` without comment.
- **Formatting:** Prettier (no debates).
- **Linting:** ESLint with `eslint-plugin-security`.
- **Testing:** 100% coverage required on `packages/crypto`. All API endpoints require integration tests including attack scenarios.
- **Documentation:** JSDoc on every public function. ADR in `/docs/adr/` for every architectural decision.

---

## Git workflow

We follow **Git Flow** with branch protection:

- `main` — production, protected, requires PR + 1 review + linear history
- `develop` — active integration branch (default branch)
- `feat/*` — features, branch from `develop`
- `fix/*` — bug fixes, branch from `develop`
- `security/*` — security patches, expedited review, branch from `main`
- `docs/*` — documentation only
- `chore/*` — tooling, CI, dependency updates

### Commit message format (Conventional Commits — enforced by commitlint)