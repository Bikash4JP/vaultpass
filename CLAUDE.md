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

```
feat(crypto): replace Math.random with crypto.getRandomValues for IV generation

Math.random is not cryptographically secure and was flagged in the security
audit. This switches all IV generation to crypto.getRandomValues(), ensuring
compliance with engineering rule #3.

Refs: #42
Security: fixes weak IV generation
```

**Allowed types:**

| Type | When to use |
|------|-------------|
| `feat` | New user-facing feature |
| `fix` | Bug fix |
| `security` | Security patch or hardening |
| `test` | Adding or correcting tests |
| `docs` | Documentation only |
| `chore` | Tooling, CI, dependency updates |
| `refactor` | Code restructuring with no behaviour change |
| `perf` | Performance improvement |

---

## Tech stack (planned)

| Layer | Technology |
|-------|-----------|
| Monorepo | pnpm workspaces |
| Mobile | React Native + Expo (TypeScript) |
| Web | React + Vite (TypeScript) |
| Backend | Node.js + Express (TypeScript) |
| Database | PostgreSQL + Prisma |
| Key derivation | Argon2id |
| Encryption | AES-256-GCM |
| Auth | JWT + refresh token rotation |
| 2FA | RFC 6238 TOTP |
| API hosting | Railway |
| Web hosting | Vercel |
| Mobile builds | Expo EAS |

Any change to this stack requires an ADR in `/docs/adr/` and an entry in `DEPENDENCY.md`.

---

## How to work with me (Claude)

- **Plan before coding.** For any non-trivial task, outline the approach and confirm it before writing code. Ask if uncertain.
- **Cite the rules.** When making a security-relevant decision, reference the specific engineering rule from this file (e.g. "Rule #3 — no Math.random").
- **Ask before adding dependencies.** No new package without a documented justification ready for `DEPENDENCY.md`.
- **Write tests alongside code.** Do not deliver a feature without its tests. `packages/crypto` requires 100% coverage — no exceptions.
- **Use Conventional Commits.** Every commit message must follow the format above. commitlint will reject non-conforming messages.
- **Never suggest committing directly to `main`.** All work flows through `develop` via a PR with at least one review.

---

## Current focus

**M0 — Foundation** is underway. The initial repository scaffolding was completed in commit `5f64a59` (policies, license, documentation stubs).

Immediate next steps:

1. Build out the `/docs` folder — write all founding documents listed above as full markdown files.
2. Set up the pnpm monorepo structure (`packages/crypto`, `packages/mobile`, `packages/web`, `apps/api`).
3. Wire up tooling: TypeScript strict config, ESLint, Prettier, commitlint, Husky pre-commit hooks.