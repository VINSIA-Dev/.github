# VINSIA Ecosystem AI & Developer Instructions

When working on any repository within the VINSIA ecosystem (`vinsia-store`, `vinsia-auth`, `vinsia-ai`, `vinsia-cloud`, `vinsia-web`):

## 1. VINSIA SSO & Auth Standards
- Centralized auth is handled by **VINSIA ID** (`auth.vinsia.web.id`) via OAuth 2.0 (RFC 6749).
- Master session is long-lived (7-30 days, HTTP-only cookie). Local platform sessions are 2-5 hours.
- RBAC is **App-Owned Granular Permissions**: Super Admin (`*`) bypasses permissions; other roles MUST check granular permissions stored in the local platform's `roles` table.
- Real-time profile/security changes are delivered via webhooks signed with HMAC SHA-256 (`X-Vinsia-Signature`).

## 2. API Conventions
- URIs: Kebab-case, RESTful plural resources (`/api/v1/products`, `/admin/api/product-secrets`).
- Non-CRUD actions: Explicit action verbs (`/checkout/process`, `/qris/create`, `/auth/vinsia/webhook`).
- JSON payload keys: Strictly `snake_case`.
- Response format: Standard `{ "status": "success"|"error", "message": "...", "data": ... }`.

## 3. Anti-AI Design System
- Matte dark neutrals (`#07080A`, `#0B0E14`, `#0F1218`), 1px hairline borders (`#1A2230`), single brand accent (`#E28D38`).
- Strictly reject AI-slop: NO unnecessary purple/cyan gradient meshes, floating pill badges, heavy frosted glassmorphism, or cliché AI marketing copy.
- Monospace font strictly for tokens, IDs, code, and logs. Clean geometric sans-serif for content.
- Ensure WCAG AAA contrast in both dark and light modes.

## 4. Engineering Standards
- Minimal, surgical diffs with zero breaking changes.
- Root cause diagnosis first; no hacky workarounds.
- Production is deployed from `main`, Staging from `staging`.
- Never hardcode secrets. Always use environment variables (`.env`).
