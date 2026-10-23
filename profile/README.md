<div align="center">

  <img src="https://raw.githubusercontent.com/VINSIA-Dev/.github/main/profile/assets/vinsia-banner.svg" alt="VINSIA Developer Ecosystem" width="100%" />

  <br />
  <br />

  <p align="center">
    <a href="https://vinsia.web.id">
      <img src="https://img.shields.io/badge/Production-Operational-10B981?style=for-the-badge&logo=statuspage&logoColor=white" alt="Production Status" />
    </a>
    <a href="https://auth.vinsia.web.id">
      <img src="https://img.shields.io/badge/Identity-OAuth_2.0_PKCE-0F172A?style=for-the-badge&logo=auth0&logoColor=E28D38" alt="OAuth2 Identity" />
    </a>
    <a href="https://github.com/VINSIA-Dev">
      <img src="https://img.shields.io/badge/Architecture-Distributed_Ecosystem-0F172A?style=for-the-badge&logo=diagram-next&logoColor=38BDF8" alt="Architecture" />
    </a>
    <a href="https://vinsia.web.id">
      <img src="https://img.shields.io/badge/Design-Anti--AI_System-E28D38?style=for-the-badge&labelColor=090B0E" alt="Anti-AI Design" />
    </a>
  </p>

  <p align="center">
    <strong>Architecting Modern Digital Ecosystems. Deploy. Connect. Scale.</strong><br />
    Official engineering organization and software ecosystem for <strong>VINSIA</strong> platforms.
  </p>

  <p align="center">
    <a href="https://vinsia.web.id">🌐 Portal</a> •
    <a href="https://auth.vinsia.web.id">🔐 VINSIA ID</a> •
    <a href="https://store.vinsia.web.id">🛒 Store</a> •
    <a href="https://ai.vinsia.web.id">⚡ AI Engine</a> •
    <a href="https://cloud.vinsia.web.id">☁️ Cloud</a> •
    <a href="https://studio.vinsia.web.id">🎨 Studio</a>
  </p>

</div>

---

### 🏛️ Executive Overview

**VINSIA** is a modern software house and technology collective delivering enterprise-grade digital platforms, automated licensing commerce, centralized identity infrastructure, and high-concurrency cloud systems.

Every platform in the ecosystem operates under strict architectural isolation with centralized authentication, resilient event-driven synchronization, and an unyielding commitment to precision craftmanship and zero-downtime reliability.

---

### 🌐 Ecosystem Platforms & Repositories

| Platform & Service | Repository | Production Gateway | Stack & Runtime | Role & Capabilities |
| :--- | :--- | :--- | :--- | :--- |
| **🌐 VINSIA Web** | [`vinsia-web`](https://github.com/VINSIA-Dev/vinsia-web) | [`vinsia.web.id`](https://vinsia.web.id) | `Next.js 16` • `TypeScript` • `Tailwind` | Master ecosystem portal, unified cross-service dashboard & company profile |
| **🔐 VINSIA Auth** | [`vinsia-auth`](https://github.com/VINSIA-Dev/vinsia-auth) | [`auth.vinsia.web.id`](https://auth.vinsia.web.id) | `Laravel 11` • `OAuth2 PKCE` • `Redis` | Central Identity Provider (IdP), root SSO session & HMAC signed webhooks |
| **🛒 VINSIA Store** | [`vinsia-store`](https://github.com/VINSIA-Dev/vinsia-store) | [`store.vinsia.web.id`](https://store.vinsia.web.id) | `Laravel 11` • `MySQL` • `Midtrans/QRIS` | Digital software solutions, automated licensing & instant checkout |
| **⚡ VINSIA AI** | [`vinsia-ai`](https://github.com/VINSIA-Dev/vinsia-ai) | [`ai.vinsia.web.id`](https://ai.vinsia.web.id) | `Docker` • `Node.js / Python` • `FastAPI` | Autonomous AI gateway, model routing, billing meters & conversational bots |
| **☁️ VINSIA Cloud** | [`vinsia-cloud`](https://github.com/VINSIA-Dev/vinsia-cloud) | [`cloud.vinsia.web.id`](https://cloud.vinsia.web.id) | `Systemd` • `Nginx` • `Linux Kernel` | Server telemetry, reverse proxy routing, backup automation & process health |
| **🎨 VINSIA Studio** | [`vinsia-studio`](https://github.com/VINSIA-Dev/vinsia-studio) | [`studio.vinsia.web.id`](https://studio.vinsia.web.id) | `Canvas API` • `WebGL` • `React` | Online photobooth creator, canvas rendering engine & media exports |

---

### 📐 Core Engineering & Architectural Pillars

```
                     ┌──────────────────────────────────────────────┐
                     │          VINSIA MASTER IDENTITY              │
                     │          (auth.vinsia.web.id)                │
                     └──────────────────────┬───────────────────────┘
                                            │ OAuth 2.0 PKCE / HMAC Webhooks
        ┌───────────────────┬───────────────┴───────────────┬───────────────────┐
        ▼                   ▼                               ▼                   ▼
┌───────────────┐   ┌───────────────┐               ┌───────────────┐   ┌───────────────┐
│   PORTAL &    │   │ VINSIA STORE  │               │   VINSIA AI   │   │ VINSIA STUDIO │
│   DASHBOARD   │   │  (E-Commerce) │               │   (Gateway)   │   │  (Media/FX)   │
└───────────────┘   └───────────────┘               └───────────────┘   └───────────────┘
```

#### 1. Centralized Identity with Local Granular RBAC
* **Unified Single Sign-On (SSO)**: Powered by standard OAuth 2.0 Authorization Code Grant with PKCE. Master sessions persist across all `.vinsia.web.id` subdomains via secure root HTTP-only cookies.
* **App-Owned Granular Permissions**: Client services retain absolute control over their local feature gates and permissions matrix. The central IdP issues identity; each client application manages business authorization.

#### 2. Real-Time Event-Driven Synchronization
* **Cryptographic Webhooks**: Any profile mutation or credential rotation on the Auth server is immediately dispatched to registered ecosystem applications using `X-Vinsia-Signature` (HMAC SHA-256).
* **Idempotent Consumers**: Microservice receivers process events with duplicate-key protection and dead-letter queues (DLQ), ensuring data consistency without race conditions.

#### 3. Anti-AI Design Philosophy
* **Rejection of Visual Slop**: We strictly prohibit bloated gradient meshes, floating pill badges, low-contrast text, and illegible card soup.
* **VINSIA Visual Token Spec**:
  * **Surfaces**: Deep matte obsidian (`#07090C`, `#0B0E14`, `#0E1219`).
  * **Borders**: 1px sharp hairline structure (`#1F2633`).
  * **Accent**: Distinct brand amber-gold (`#E28D38` / `#F39A45`).
  * **Typography**: Geometric sans-serif for UI layout, monospace strictly for tokens, IDs, and code.
  * **Accessibility**: Strict WCAG AAA contrast compliance across light and dark themes.

#### 4. Resilient Production Engineering
* **Root-Cause First**: Zero superficial workarounds. Diagnoses prioritize root-cause resolution over patch-on-patch degradation.
* **Zero Downtime Deployments**: Hot-reload configurations, atomic symlink deploys, and process supervision via `systemd` and `aaPanel`.

---

### 🛠️ Technology Stack & Toolchain

<div align="center">

| Layer | Technologies & Frameworks |
| :--- | :--- |
| **Frontend & UI** | ![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white) ![React](https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white) ![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=flat-square&logo=framer&logoColor=white) |
| **Backend & APIs** | ![Laravel](https://img.shields.io/badge/Laravel_11-FF2D20?style=flat-square&logo=laravel&logoColor=white) ![PHP](https://img.shields.io/badge/PHP_8.3-777BB4?style=flat-square&logo=php&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) ![Python](https://img.shields.io/badge/Python_3.12-3776AB?style=flat-square&logo=python&logoColor=white) ![REST](https://img.shields.io/badge/REST_API-0284C7?style=flat-square&logo=fastapi&logoColor=white) |
| **Database & Cache** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) |
| **DevOps & Infra** | ![Ubuntu](https://img.shields.io/badge/Ubuntu_Linux-E95420?style=flat-square&logo=ubuntu&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) |

</div>

---

### 📚 Standards & Agent Instructions

All contributors and autonomous AI agents working in this organization must adhere to our centralized specifications:

* 📘 **[Engineering Guidelines (`GUIDELINES.md`)](https://github.com/VINSIA-Dev/.github/blob/main/GUIDELINES.md)**: Architectural specs, RESTful URI kebab-case conventions, JSON `snake_case` envelopes, and UI design rules.
* 🤖 **[Autonomous AI Agent Rules (`AGENTS.md`)](https://github.com/VINSIA-Dev/.github/blob/main/AGENTS.md)**: Operational boundaries, minimal-diff mandates, and security protocols for Claude Code, Hermes, Copilot, and Cursor.
* 📋 **[Copilot Instructions (`.github/copilot-instructions.md`)](https://github.com/VINSIA-Dev/.github/blob/main/.github/copilot-instructions.md)**: Prompt configurations and workspace rules for AI-assisted coding.

---

### 🔒 Security & Vulnerability Reporting

Security is foundational to our ecosystem. If you discover a security vulnerability within any VINSIA platform or service:

1. **Do not open a public issue.**
2. Send an advisory detailing reproduction steps to: **`firnansyah15@gmail.com`**.
3. We acknowledge reports within 24 hours and issue patch advisories through coordinated disclosure.

---

<div align="center">

  <sub>Crafted with precision by <strong>VINSIA Engineering Team</strong> • Owned &amp; Directed by <strong>Vicky Firnansyah</strong></sub><br />
  <sub>&copy; 2026 VINSIA. All rights reserved.</sub>

</div>
