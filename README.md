# Trip Receipts — travel expense PWA

Snap receipt photos, log expenses (date, type, local amount, USD amount), and export everything as an .xlsx spreadsheet plus a PDF of all receipt images. Works fully offline once installed.

## Files

- `index.html` — the whole app (UI, IndexedDB storage, xlsx + PDF export)
- `manifest.webmanifest` — makes it installable
- `sw.js` — service worker; caches the app and the two CDN libraries so it works offline
- `icon-192.png`, `icon-512.png` — app icons

## Deploy on GitHub Pages (once, ~3 minutes)

1. Create a new GitHub repo, e.g. `trip-receipts`.
2. Upload all five files to the repo root (web UI: *Add file → Upload files*).
3. Repo *Settings → Pages → Source*: select branch `main`, folder `/ (root)`. Save.
4. Wait a minute; your app is live at `https://<your-username>.github.io/trip-receipts/`.

## Install on your phone (before the trip, while online)

- **iPhone (Safari):** open the URL → Share → *Add to Home Screen*.
- **Android (Chrome):** open the URL → menu → *Install app* (or *Add to Home screen*).

Open it once while online so the service worker caches everything; after that it works with no connectivity.

## Using it

1. Tap **Snap receipt photo** — the camera opens directly. Photos are auto-compressed (~1500 px JPEG) before being stored.
2. Fill date (defaults to today), expense type, currency, and local amount.
3. Enter the exchange rate once per currency (1 local unit = X USD); the USD amount auto-fills and stays editable. The rate is remembered per currency.
4. **Save expense.** Tap any entry to edit it; ✕ deletes it.
5. **Spreadsheet (.xlsx)** exports columns: Date, Expense Type, Amount (Local Currency), Currency, Amount (USD), with a total row.
6. **Receipts PDF** exports one receipt photo per A4 page, captioned with date, type, and amounts.

## Notes

- Data lives in IndexedDB on the phone. iOS can evict PWA storage after long disuse — export your xlsx/PDF at the end of each trip (or every few days on long ones) rather than treating the phone as permanent storage.
- Everything is client-side; no server, no accounts, photos never leave the device except in your exports.
