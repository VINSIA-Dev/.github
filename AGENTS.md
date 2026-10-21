# VINSIA Autonomous AI Agent Guidelines

This file provides system instructions for AI coding agents (Claude Code, Hermes, Cursor, Copilot, Codex, Aider) operating on any repository in the **VINSIA-Dev** organization.

For the full detailed specification, read `GUIDELINES.md`.

---

## Non-Negotiable Rules

1. **Root Cause First & Minimal Diffs**:
   - Understand the underlying system and identify the real root cause before writing or editing code.
   - Deliver minimal, surgical edits. Do not refactor unrelated files or introduce breaking changes.

2. **Single Sign-On (SSO) & Permissions**:
   - Central authentication is at `auth.vinsia.web.id` using OAuth 2.0.
   - Master sessions are 7-30 days in browser cookies; local sessions are 2-5 hours.
   - RBAC is **App-Owned Granular Permissions**: only super admin has wildcard `*` access; all other staff roles must strictly check granular permissions in the local database `roles` table.
   - Any profile/password change in Auth must trigger realtime webhooks (`X-Vinsia-Signature` HMAC SHA-256) to client platforms.

3. **API & Data Standards**:
   - URI paths MUST be kebab-case and RESTful (`/api/v1/products`, `/admin/api/product-secrets`, `/auth/vinsia/webhook`).
   - JSON payload attributes MUST be `snake_case`.
   - Standard envelope: `{ "status": "success"|"error", "message": "...", "data": ... }`.

4. **UI Design (Anti-AI Slop)**:
   - Matte dark neutrals (`#07080A`, `#0B0E14`, `#0F1218`), 1px hairline borders (`#1A2230`), single accent (`#E28D38`).
   - Strictly reject purple/cyan mesh gradients, floating pill badges, heavy glassmorphism, and AI boilerplate text.
   - High contrast (WCAG AAA) across dark and light themes.

5. **Deployment & Branch Rules**:
   - `main` branch deploys to **Production**.
   - `staging` branch deploys to **Staging**.
   - Zero downtime: never kill essential server ports or reboot the VPS.
