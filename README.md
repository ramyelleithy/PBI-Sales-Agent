# PBI Sales Agent — MAYA

> **⚠️ LEGACY — this repo is no longer the source of truth.**
> All content here has been merged into **[`ramyelleithy/MAYA-Knowledge`](https://github.com/ramyelleithy/MAYA-Knowledge)** (`12_Implementation/Product_Skills/` and `12_Implementation/Infrastructure/`) as of 2026-07-23. That repo is now the single source of truth for how MAYA thinks and works — this one existing separately is what caused MAYA's sales-skill specs to go untracked and rediscovered mid-project. Do not edit files here going forward; edit the merged copies in `MAYA-Knowledge` instead. This repo is kept only for historical reference.

**MAYA** is the AI Sales Executive of **Propify Brokerage Agency** (Egypt).

She handles the complete customer journey on WhatsApp — from the first message to booking qualification — covering the entire Egyptian real estate market, not a single developer.

> Propify is a brokerage. MAYA's scope is the full market.

---

## What this repo contains

This is the **source of truth for how MAYA thinks and works**.

It does NOT store project operational content (brochures, price lists, images). That lives in Google Drive.

| File | Purpose |
|---|---|
| `Architecture` | Full system design, runtime flow, Phoenix Server infrastructure, Three-Tier Knowledge Model, Project Code convention |
| `MAYA_System_Prompt` | MAYA's core instruction set fed to OpenAI at runtime |
| `MAYA_AI_CONSTITUTION` | Complete sales skills, Arabic terminology, detailed behavior rules |
| `PBA \| Propify Brain & AI` | MAYA's persona, tone, 5 operating rules, Micro-RAG setup (Arabic) |
| `Propify_Sales_Methodology` | Propify's consultative sales philosophy and 8-step process |
| `PRIVACY_POLICY.md` | Customer data privacy policy (WhatsApp / Meta Ads) |
| `CHANGELOG.md` | Version history and what's been built |

---

## Source of Truth

| What | Where |
|---|---|
| How MAYA thinks | **This repo (GitHub)** |
| What MAYA knows | **Google Drive** → `Propify Property Intelligence/Projects/` |
| Workflow automation | **n8n**, self-hosted on **Phoenix Server** |
| Conversation engine | **OpenAI** |

---

## Infrastructure

n8n runs self-hosted on **Phoenix Server** — a dedicated VPS that is the shared foundation for MAYA and future Phoenix OS agents, not a single-purpose n8n box. See `Architecture` → "Infrastructure — Phoenix Server" for the full stack (Docker, PostgreSQL, Nginx + SSL, Portainer) and folder structure.

---

## Owner

**Ramy El-Laithy** — Founder, Propify Brokerage Agency
