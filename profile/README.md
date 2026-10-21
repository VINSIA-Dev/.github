# VINSIA Developer Ecosystem

Official engineering organization and software ecosystem for **VINSIA** platforms.

## Active Ecosystem Services
- **[VINSIA Web](https://www.vinsia.web.id)**: Official portal & company profile (`vinsia-web`).
- **[VINSIA Auth](https://auth.vinsia.web.id)**: Central SSO & identity provider (`vinsia-auth`).
- **[VINSIA Store](https://store.vinsia.web.id)**: Modern digital e-commerce & services platform (`vinsia-store`).
- **[VINSIA AI](https://ai.vinsia.web.id)**: AI gateway, chatbot & billing infrastructure (`vinsia-ai`).
- **[VINSIA Cloud](https://vinsia.web.id)**: Cloud infrastructure & management (`vinsia-cloud`).

## Core Architecture & Engineering Principles
1. **Centralized Identity with Local Granular RBAC**: VINSIA ID handles OAuth 2.0 authentication, while granular permissions are app-owned.
2. **Real-time Event Synchronization**: Zero-latency cross-platform updates via secure HMAC SHA-256 signed webhooks.
3. **Anti-AI Design Philosophy**: High-contrast, matte-neutral aesthetic with precision typography and zero AI-slop visual artifacts.
4. **Resilient Production Engineering**: Minimal, surgical diffs, root-cause debugging, and zero-downtime deployments.

Refer to [`GUIDELINES.md`](./GUIDELINES.md) and [`AGENTS.md`](./AGENTS.md) for full engineering specifications.
