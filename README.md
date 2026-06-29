# Jefferson Health Plans — Member Consent Portal (Demo)

A clickable, front-end-only prototype of JHP's **internal customer-service portal** for managing member
data-sharing consent under **CMS-0057** (the CMS Interoperability & Prior Authorization Final Rule).

Built for the **Learning & Development team** to click through the live experience and create training
content for the customer-service team. No backend, no real member data — everything runs in the browser.

**Live demo:** `https://hike-health.github.io/jhp-consent-portal/` *(available once Pages is enabled — see below)*

---

## What it covers

The portal implements the two member-consent models CMS-0057 requires payers to support:

| Screen | CMS-0057 mapping | Consent model |
| --- | --- | --- |
| **Share data with healthcare providers** | Provider Access API | **Opt-out** (sharing on by default) |
| **Transfer data from other health plans** | Payer-to-Payer API | **Opt-in** (member must opt in per prior plan) |

### Clickable flows
- **Sign in** → CSR landing page
- **Member search** — by name, member ID, or phone, with live-filtered results and recent members
- **Member profile** — demographics + current consent status for both consent types
- **Provider consent** — toggle opt-in/opt-out, required CSR attestation, confirmation + toast
- **Payer-to-Payer transfer** — multi-select prior plans, attestation, submission with reference ID
- **Manage member consents** — plans grouped by Opted-in / Opted-out / Expired
- **Review consent** — per-plan detail (granted date, last transfer, status, revocation, opt-in history)
- **Opt-out / revoke** — confirmation modal with required admin attestation
- **Plan transfer-status** detail page
- **Search by plan** within a member's consents
- **Toast notifications** for every consent change

> Sample members: **John Doe** (ID `123456`) and **Sarah Brown** (ID `456789`).
> All data is fictional and resets on logout/refresh.

---

## Deploy to the HIKE-HEALTH org (one step)

This folder is a **ready-to-push static site** — it's already a committed git repo. Pick one path.

### Option A — GitHub CLI (fastest)
Requires the [`gh` CLI](https://cli.github.com/) signed in to an account with access to the `HIKE-HEALTH` org.

```bash
cd "jhp-consent-portal"

# Create the repo under HIKE-HEALTH and push this folder
gh repo create HIKE-HEALTH/jhp-consent-portal --public --source=. --remote=origin --push

# Turn on GitHub Pages (serves the root of the main branch)
gh api -X POST repos/HIKE-HEALTH/jhp-consent-portal/pages -f "source[branch]=main" -f "source[path]=/"
```

Your shareable link (live in ~1 minute):
**https://hike-health.github.io/jhp-consent-portal/**

### Option B — plain git + the web UI
```bash
cd "jhp-consent-portal"
git remote add origin https://github.com/HIKE-HEALTH/jhp-consent-portal.git
git push -u origin main
```
Then on GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch" → Branch: `main` / `(root)` → Save.**
The link appears at the top of that page after ~1 minute.

> Private org? Either make the repo public (Pages link is public regardless), or use a GitHub
> Team/Enterprise plan that allows Pages on private repos.

---

## Run locally
It's a single static file — just open `index.html` in any browser, or:
```bash
cd "jhp-consent-portal" && python3 -m http.server 8080
# visit http://localhost:8080
```

## Files
- `index.html` — the entire app (HTML + CSS + JS, no dependencies)
- `.nojekyll` — tells GitHub Pages to serve files as-is
- `README.md` — this file

---
*Internal training demonstration only. Not a production system and not connected to any member data source.*
