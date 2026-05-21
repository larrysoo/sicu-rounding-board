# Larry's SICU rounds

A self-contained ICU rounding board: hemodynamics (VIS / vasoactives / MCS), respiratory, ABG with 6-step acid-base interpretation, renal (KDIGO / RRT / cumulative balance), nutrition (NRS-2002 / EN-PN / GI), neuro (GCS / RASS / CPOT / pupils), cultures with S/I/R, antibiotic resistance flagging, plan-tracking per organ, board view, and printable round sheet.

Single-page web app. All data stored in your browser's `localStorage` — nothing leaves the device. Works offline once installed as a PWA.

---

## Deployment — GitHub Pages

### One-time setup

1. Create a new GitHub repo named **`sicu-rounding-board`** (or any name; the URL will be `https://<account>.github.io/<repo>/`).
2. Upload all files in this folder to the repo root:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
   - `.nojekyll`
   - `README.md` (this file)
3. Go to repo **Settings → Pages**.
4. Under **Source**, select **Deploy from a branch**, branch **`main`** (or `master`), folder **`/ (root)`**. Save.
5. Wait ~1 minute. Refresh the Pages settings page — the URL appears at the top, like `https://your-username.github.io/sicu-rounding-board/`.
6. Open that URL on any device. Bookmark it.

### Updating the app

Edit any file, commit, push. GitHub Pages redeploys in ~1 minute. The service worker will pick up changes on next reload (you may need to refresh twice — first updates cache, second uses new cache). To force-update, bump `CACHE` version in `sw.js`.

---

## Install as standalone app

### iPhone / iPad

1. Open the GitHub Pages URL in **Safari** (not Chrome — only Safari supports PWA install on iOS).
2. Tap the **Share** button (square with up-arrow).
3. Scroll down, tap **Add to Home Screen**.
4. Confirm. The app appears on your Home Screen with the SICU icon.
5. Open from Home Screen — runs fullscreen, no Safari chrome, no URL bar. Works offline.

### Android

1. Open the URL in **Chrome**.
2. Three-dot menu → **Install app** (or **Add to Home Screen**).
3. Confirms automatically. Works offline.

### Mac / Windows desktop

1. Open the URL in **Chrome** or **Edge**.
2. Look for the **install icon** in the URL bar (right side, looks like a monitor with down-arrow), or three-dot menu → **Install Larry's SICU rounds…**
3. Confirms and adds to Applications / Start Menu. Runs as standalone window.

### macOS Safari (Sonoma+)

1. Open in Safari.
2. File → **Add to Dock…**
3. Standalone window app added to Dock.

---

## Data management

- **All data stored locally** in your browser's `localStorage`. Different browsers / devices = separate data. Same browser across visits = persistent.
- Use **Export** button in the toolbar to download your data as JSON. Save to iCloud / Dropbox / Google Drive for backup.
- Use **Import** to load a previously exported JSON. **Warning: import replaces all current data.**
- **Reset** wipes local data and reloads the 3 demo patients.

### Cross-device sync workflow

Since there's no backend, manual sync via JSON:

- End of shift on iPad → Export JSON → email to yourself or save to cloud.
- Next shift on desktop → Import JSON.
- Or just keep one device as the "source of truth" and view-only on others.

---

## Privacy & compliance

- **Do not enter real patient names, national ID numbers, or full MRNs.** Use bed number + internal codes only.
- This app is a **personal working notebook / teaching tool / SBAR draft helper** — not a substitute for your hospital's official medical record system.
- All data lives on your device. No network calls except for loading the icon font from CDN on first launch (then cached offline). No analytics, no tracking, no server.
- If you need true cross-device sync with real patient data, that requires a hospital-sanctioned IT solution with proper encryption, access controls, and regulatory compliance. This app is intentionally local-only to avoid those concerns.

---

## Browser support

Tested on:
- Safari 17+ (macOS, iOS, iPadOS)
- Chrome 120+ (macOS, Windows, Android)
- Edge 120+ (Windows)
- Firefox 120+ (limited PWA install support)

Requires modern browser with `localStorage`, ES2017+, CSS Grid, and service worker support.

---

## File reference

| File | Purpose |
|---|---|
| `index.html` | Main app — HTML + CSS + JS in one file |
| `manifest.json` | PWA metadata (name, icons, theme color, display mode) |
| `sw.js` | Service worker — offline cache |
| `icon-192.png` | App icon 192×192 |
| `icon-512.png` | App icon 512×512 |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |
| `README.md` | This file |

---

## Version

v13.2B — Wave 2B (Nutrition + Board view + JSON I/O + tri-view toggle)

Features:
- 11-drug vasoactive catalog with VIS auto-calc
- 5-device MCS catalog (VA/VV-ECMO, Impella, LVAD, IABP)
- ABG 6-step acid-base interpretation (Winters, AG, Δ/Δ, P/F, A-a)
- P/F vs PEEP dual-axis 7-day chart with ARDS severity bands
- KDIGO staging, ROSE phase, cumulative balance
- Neuro: GCS-T, CPOT 4 subscores, pupil exam with anisocoria/RAPD, RASS labels
- Cultures with S/I/R sensitivities, antibiotic resistance flagging
- PMH 5 categories, surgical interventions timeline
- Nutrition: NRS-2002, EN/PN plan with route, kcal/protein achievement %, GI symptoms, RQ
- Board view with patient cards
- Print sheet with 8 sections including embedded P/F vs PEEP chart
- Export / Import JSON
- Offline-capable PWA

---

Built collaboratively with Claude.
