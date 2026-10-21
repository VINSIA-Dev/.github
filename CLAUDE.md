# VINSIA Claude Code & Agent Guidelines

See `GUIDELINES.md` for full ecosystem standards.

## Quick Reference
- **SSO**: OAuth 2.0 via `auth.vinsia.web.id`. Master session 7-30 days; local platform session 2-5 hours.
- **RBAC**: App-Owned Granular Permissions. Superadmin `*`; other roles obey local `roles` permissions JSON.
- **Webhooks**: Signed via HMAC SHA-256 in `X-Vinsia-Signature`.
- **API**: Kebab-case URIs, `snake_case` JSON keys, standard `{ status, message, data }` responses.
- **Design**: Anti-AI Slop. Matte neutrals, hairline borders, `#E28D38` accent, high contrast.
- **Git**: `main` = Production, `staging` = Staging. Minimal, surgical diffs.
