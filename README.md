# Benecard PBF — Implementation Setup (Prototype)

Preliminary HTML/CSS/JS prototype reimagining Benecard PBF's 19-tab Implementation
Guide workbook as a guided, step-by-step configuration workspace — built inside a
Salesforce Headless 360-flavored app shell.

**Status:** Preliminary / mock data only. No live Salesforce connection yet.

## What's in this prototype

- **App shell** — global header, icon rail, contextual sidebar, breadcrumb, and
  page footer, so the wizard sits inside something that reads as a real app.
- **Implementation Config Wizard** — tabs 1–10 of the source workbook
  (`Client-TPA-RptOpts` through `Copays_1`), re-labeled in plain language, with:
  - Automatic step status (Not Started / In Progress / Complete) instead of
    manual red/yellow/green color-coding
  - Plain-language help tooltips on PBM jargon (DAW, GPI, MOOP, ERISA, etc.)
  - Repeatable data (TPAs, contacts, billing groups, plans, copay rules) as
    stacked add/remove cards instead of wide spreadsheet rows
  - Searchable type-ahead pickers for long reference lists (CPNs, formularies,
    drug categories) instead of long native dropdowns
  - Multi-plan support and TPA/broker relationship **end-dating** — both
    called out directly from customer discovery-call pain points
- **Onboarding tour** — a 6-slide walkthrough of the above, shown on first
  visit (remembered via `localStorage`), reopenable anytime from the header.
- **AI Assist** — a floating action button that opens an overlay offering to
  pre-fill known fields from public sources, with a clear opt-out and a
  "Help needed? Talk to your implementation specialist" escalation path.

## Local preview

No build step — it's a single static HTML file. Either:

```bash
open index.html
```

or serve it locally:

```bash
npx serve .
```

## Deploying to Vercel

1. Push this folder to a new GitHub repository.
2. In Vercel: **Add New → Project → Import** the GitHub repo.
3. Framework Preset: **Other** (static site) — no build command, no install
   command needed.
4. Output directory: leave as root (`.`).
5. Deploy. Vercel will serve `index.html` at the project's root URL.

`vercel.json` in this folder is a minimal config (clean URLs); no changes
needed for a first deploy.

## Known scope limits (flag before client review)

- Tabs 11–19 of the source workbook are not yet built.
- Cross-references between steps (e.g. Plan Name pulling from the Plans step,
  Billing Group pulling from Contacts & Billing) are labeled but not wired.
- The Drug Coverage category picker (tab 5) stops at category selection; the
  per-category mail/retail rule builder is not yet built.
- AI Assist and the onboarding tour are UI concepts only — no backend calls.
- All data is mocked; nothing persists on refresh.
