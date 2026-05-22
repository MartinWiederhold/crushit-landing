# CrushIt — Landingpage

Statische Landingpage für die CrushIt iOS-App (vormals Study AI).

**Live:** https://crushit-beta.vercel.app

## Inhalt

- `index.html` — Single-Page mit Hero, Features, Pricing, Testimonials, CTA, Footer
- Rechtssektionen (toggelbar via Hash-Routing):
  - `/#datenschutz` — DSGVO-konforme Datenschutzerklärung
  - `/#impressum` — § 5 TMG
  - `/#agb` — Nutzungsbedingungen + Abo-Modalitäten
- `vercel.json` — Cleanup + Security-Headers
- `_style.css` ist inline im HTML (kein Build-Step)

## Deployment

Automatischer Deploy via Vercel auf jeden `main`-Push.

## Tech

Vanilla HTML/CSS/JS. Keine Build-Tools. DM Serif Display + Inter via Google
Fonts CDN.
