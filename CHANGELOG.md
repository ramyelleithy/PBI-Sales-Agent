# CHANGELOG

---

## [1.1.0] — 2026-07-12

### Infrastructure Migration: Phoenix Server

**Server provisioning:**
- Provisioned Phoenix Server (Contabo Cloud VPS, Ubuntu 24.04 LTS, 4 vCPU / 8GB RAM / 75GB NVMe, auto-backup enabled)
- Hardened base OS: non-root sudo user (`propify`), SSH key-only auth (password login disabled), UFW firewall (22/80/443), Fail2Ban

**Container platform:**
- Installed Docker Engine + Docker Compose
- Installed Portainer CE for visual container monitoring
- Established `/opt/phoenix` folder structure: `compose/` (one subfolder per service), `data/` (bind-mounted service data), `backups/`, `logs/`, `scripts/`
- Adopted architectural rules: one folder per service, no monolithic docker-compose files, every service ships with `.env` + `docker-compose.yml` + `README.md` from day one

**n8n deployment:**
- Deployed `n8n` + `PostgreSQL` via Docker Compose (replacing the default SQLite) under container names `phoenix-n8n` / `phoenix-postgres` on a dedicated `phoenix-net` Docker network
- Configured `.env`-based secrets, bind-mounted volumes, `unless-stopped` restart policy, and health checks on both containers
- n8n internal port bound to `127.0.0.1` only — never exposed directly to the internet
- Registered `subdomain` `n8n.propify-egy.com`, configured Nginx as reverse proxy, and issued a Let's Encrypt/Certbot SSL certificate (auto-renewing)
- Redis deliberately deferred — no current need for Queue Mode or multiple workers

**Workflow migration (OpenHosst → Phoenix Server):**
- Exported and re-imported the "MAYA - WhatsApp Sales Agent" `n8n` workflow unchanged
- Re-created and re-linked all credentials on the new instance: Google Drive (new Service Account key), Google Sheets, OpenAI (new API key)
- Updated the Meta WhatsApp Business API webhook Callback URL to `https://n8n.propify-egy.com/webhook/whatsapp-webhook` and re-verified successfully
- Published the workflow and ran a full end-to-end test (pinned data + Execute workflow) — all nodes completed successfully with a correct, honest MAYA response

**Documentation:**
- Updated `Architecture` with a new "Infrastructure — Phoenix Server" section and the previously-undocumented "Naming Convention — Project Code" section

### Pending (next versions)
- Install Chatwoot (conversation monitoring + human takeover)
- Install Netdata (resource monitoring; VPS upgrade decision to be based on 85%+ sustained RAM over two weeks, not a guess)
- Resume the Three-Tier Knowledge Model work, paused during the server migration
- Continue the knowledge base and data-tooling items carried over from 1.0.0 (see below)

---

## [1.0.0] — 2026-07-10

### Initial Release (MVP)

**Architecture:**
- Defined core component stack: n8n + OpenAI + Google Drive + GitHub
- Established Three-Tier Knowledge Model (Entry Project → Pivot → Deep Dive)
- Defined Project Code naming convention for Meta Ads
- Established escalation policy (reserve / site visit / unit selection / negotiation only)

**Knowledge Base (Google Drive):**
- Created unified root folder: `Propify Property Intelligence`
- Established standard project folder structure: `Project_Bible.md + Sales_Playbook.md + Client_Files/`
- Documented 9 projects (8 active + 1 empty template flagged for deletion):
  - Margins: Sheraton Residences ✅ (official brochure)
  - Margins: Lusail Residence ✅ (official brochure)
  - Margins: Oaks ✅ (official brochure)
  - Margins: Zia ✅ (official brochure)
  - Upwyde: White Residence ⚠️ (internet sources, price conflicts documented)
  - Madinet Masr: Taj City ⚠️ (internet sources, price conflicts by phase)
  - Madinet Masr: Sarai ⚠️ (internet sources, price conflicts by phase)
  - El Batal: Rock Vera ⚠️ (internet sources, major price conflict 3.75M vs 10.7M)
  - Mountain View iCity 🚫 (empty template — not a real project, flagged for manual deletion)

**Data Tools:**
- WhatsApp Collector (Node.js + Baileys): monitoring 163 developer groups, writing to Raw_Data/WhatsApp/
- Aqarmap Scraper (Node.js + Playwright): successfully scraped التجمع الخامس → 275 unique projects after dedup
- Projects_Master (Google Sheet): pilot batch of 25 projects + 275 from scraper pending import

**Pending (next versions):**
- Import 275 Aqarmap projects into Projects_Master
- Build WhatsApp classification + approval workflow in n8n
- Verify existing n8n workflow after Drive restructure
- Expand knowledge base beyond current 8 projects
- Obtain official brochures for non-official project files
