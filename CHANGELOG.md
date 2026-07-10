# CHANGELOG

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
