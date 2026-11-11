# Zebra Doctor — Lead CRM

Source for the **Lead CRM** used to manage leads, landing pages, automations and
scoring for zebradoctor.com and its product microsites.

Live artifact: https://claude.ai/code/artifact/5cfd3c6f-eaaf-4dde-9f1f-8c4919911388

## What this repo is

A version-controlled copy of the CRM's source. The app is a single
self-contained page (`index.html`) — React 18 + htm loaded from CDN, no build
step. Opening the file in a browser runs it; data is held in the artifact's own
shared database when it runs as a published artifact, and falls back to
`localStorage` otherwise.

> The published artifact remains the live copy. Treat this repo as the
> versioned record of the source, not as the deployment target.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The whole CRM — styles, components and logic in one file |

## Modules in the app

- **Leads** — statuses New → Contacted → Engaged → Qualified → Converted /
  Disqualified / Unresponsive, with a drag-and-drop board
- **Scoring** — configurable point rules; Warm from 20, Hot from 50
- **Verification & activity** — per-microsite required checks and an
  "active" rule (key action on N days within a window)
- **Microsites** — the six Zebra Doctor tools, each with its own key action
- **Landing pages** — builder and published pages (e.g. the APPNA attendee offer)
- **Automations** — trigger → step sequences (email, SMS, call, notify, wait)
- **Compliance** — consent per channel, suppression list, quiet hours,
  contact caps and a 30-day cooldown, enforced on every send
- **Audit log** — who did what, capped at the last 500 entries

## Roles

Admin, Manager, Marketer, Sales rep, Viewer — permissions are checked in
`can(action, lead)`.

## Notes

- No secrets or lead records are stored in this file; it contains only app code.
- External dependencies: React/ReactDOM/htm via jsDelivr, Google Fonts, and the
  public NPI registry lookup (npiregistry.cms.hhs.gov).
