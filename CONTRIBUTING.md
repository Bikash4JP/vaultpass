# Contributing to VaultPass

Thank you for considering contributing to VaultPass. This document explains how we work, what we expect, and how to get your changes merged.

> **First time?** Start with issues tagged [`good-first-issue`](https://github.com/Bikash4JP/vaultpass/labels/good-first-issue).

## 📜 Code of Conduct

VaultPass adopts the [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). The short version:

- Treat everyone with respect. Assume good faith.
- Debate ideas, not people.
- Security researchers are colleagues, not adversaries.
- Discrimination or harassment of any kind results in immediate ban.

Report incidents to `conduct@vaultpass.io` *(once configured)* or directly to a maintainer.

## 🌿 Git Workflow

We follow **Git Flow** with branch protection enforced on `main`.

### Branch types

| Branch | Purpose | Branch from |
|---|---|---|
| `main` | Production. Protected. No direct push. | — |
| `staging` | Pre-release integration | `develop` |
| `develop` | Active development integration | `main` |
| `feat/*` | New feature | `develop` |
| `fix/*` | Bug fix | `develop` (or `main` for hotfix) |
| `security/*` | Security patch — expedited | `main` |
| `docs/*` | Documentation only | `develop` |
| `chore/*` | Tooling, CI, dependency updates | `develop` |

### Branch naming examples
feat/vault-item-encryption
fix/refresh-token-expiry-calculation
security/jwt-algorithm-confusion
docs/adr-001-argon2-parameters
chore/bump-typescript-5.4

## ✍️ Commit Message Standard

We use [Conventional Commits](https://www.conventionalcommits.org/). This is **enforced by `commitlint` in CI** — non-conforming commits will be rejected.

### Format

type(scope): short description [max 72 chars]
[Optional body: explain WHY, not what. The diff shows what.]
[Optional footer:]
BREAKING CHANGE: description
Refs: #issue-number
Security: CVE-XXXX-XXXX

### Allowed types

| Type | When to use | Example |
|---|---|---|
| `feat` | New feature | `feat(vault): add AES-256-GCM encryption` |
| `fix` | Bug fix | `fix(auth): correct refresh token expiry` |
| `security` | Security fix | `security(jwt): enforce RS256 over HS256` |
| `test` | Tests added/updated | `test(crypto): add IV reuse test cases` |
| `docs` | Documentation | `docs(adr): add ADR-003 Argon2id parameters` |
| `chore` | Tooling, CI, deps | `chore(deps): bump argon2 0.31.0 → 0.31.2` |
| `refactor` | No behavior change | `refactor(crypto): extract IV util` |
| `perf` | Performance | `perf(vault): batch decrypt on initial load` |

## 🔀 Pull Request Process

1. **Fork** the repo (external) or **branch** from `develop` (maintainer)
2. **Write code + tests** — tests must pass locally before opening the PR
3. **Open PR** using the PR template
4. **CI runs**: lint → type-check → unit tests → integration tests → security audit
5. **Review**: at least one maintainer approval. Founding-team PRs also require review.
6. **Resolve all comments** before merging — no merging with unresolved threads
7. **Squash merge** to `develop` for clean linear history

## ✅ Quality Standards

All code must meet these before merge:

- TypeScript strict mode — no `any`, no `@ts-ignore` without documented reason
- ESLint passing — including `eslint-plugin-security` rules
- Prettier-formatted
- Unit tests for all cryptographic functions (100% coverage on `packages/crypto`)
- Integration tests for all API endpoints, including negative/attack scenarios
- JSDoc on every public function
- Updated `CHANGELOG.md` and OpenAPI spec when applicable

## 🛡️ Security-Sensitive Changes

PRs touching authentication, encryption, key management, or any code in `packages/crypto/` follow a stricter process:

- **Additional review** from a maintainer with security expertise
- **Threat-model impact assessment** in the PR description
- **Negative test cases** (wrong key, tampered ciphertext, expired token) required
- **No "trust me" comments** — every security claim is backed by test or proof

If unsure whether your change qualifies, ask in the PR — we'd rather over-review than under-review.

## 🤔 Questions?

- General discussion → [GitHub Discussions](https://github.com/Bikash4JP/vaultpass/discussions)
- Bug reports → [Open an issue](https://github.com/Bikash4JP/vaultpass/issues/new)
- Security issues → see [`SECURITY.md`](./SECURITY.md)

---

*Thank you for helping build software people can actually trust.*
