# Sharma Customer App

Lean app 7 of 7 (33 apps → 7). One public app, **three entry links** — Sanjay's rule:

| Link | Section |
|---|---|
| For Builders | `builders/` — the Builders & GCs page |
| For Homeowners | `homeowners/` — the Homeowner Hub |
| Pickers | `pickers/` — Smart Home, HVAC and Electrical pickers inside one section |

Public, no login, no internal data, no push. The shell (front door + Pickers
section page) follows the fleet Apple style: sharma-kit v1.3 patterns, macOS
wide-screen look (`macos.css`, ≥960px), light-always on open, navy #264387 /
gold #F0A846, 18px minimum type.

## How the sources were folded in

- `builders/` and `homeowners/` are full copies of the old `sharma-builders`
  and `homeowner-hub` apps. Only path fixes: service-worker scope and
  manifest start_url/scope now point at their new paths, and the Homeowner
  Hub's three picker buttons now link in-app (`../pickers/…`) instead of the
  old picker sites.
- `pickers/smart-home-picker/`, `pickers/hvac-picker/`, `pickers/electrical-app/`
  are **byte-for-byte copies** of the three picker apps (verified by checksum,
  114 files) — content and behavior unchanged, per Sanjay's standing rule.
  The folder names keep the Electrical Picker's `../hvac-picker/` and
  `../smart-home-picker/` cross-links working exactly as before.

## Redirects from the old public URLs

Each old repo's `index.html` is now a redirect page into the matching section
below, and its `sw.js` is a self-destruct worker that clears the old caches —
links already in customers' hands keep working.

| Old URL | Lands at |
|---|---|
| sharmaelechvac.github.io/sharma-builders/ | /sharma-customer/builders/ |
| sharmaelechvac.github.io/homeowner-hub/ | /sharma-customer/homeowners/ |
| sharmaelechvac.github.io/smart-home-picker/ | /sharma-customer/pickers/smart-home-picker/ |
| sharmaelechvac.github.io/hvac-picker/ | /sharma-customer/pickers/hvac-picker/ |
| sharmaelechvac.github.io/electrical-app/ | /sharma-customer/pickers/electrical-app/ |

Old section files (assets, styles) remain in the old repos untouched; only
`index.html` and `sw.js` changed there.
