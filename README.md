# CBS Ledger – Android app (installable PWA)

Fills your CBS ledger exactly as in `CBS_ledger_New_Version_Ekyam.xlsx` (all 12 sheets, same columns, same formulas), one full ledger per Vatika.
Works offline; auto-saves to your Google Drive after every change.

## 1. One-time Google setup (≈10 min, free)
1. https://console.cloud.google.com → create a project.
2. **APIs & Services → Library**: enable **Google Drive API** and **Google Sheets API**.
3. **OAuth consent screen**: User type *External* → add your own Gmail (and any teammates) under **Test users**.
4. **Credentials → Create credentials → OAuth client ID → Web application**.
   Under **Authorized JavaScript origins** add the URL where you host the app (step 2), e.g. `https://yourname.github.io`.
5. Copy the **Client ID** (ends in `.apps.googleusercontent.com`). The app asks for it the first time you tap *Connect Google*.

## 2. Host the files (free, HTTPS required)
Upload this folder to **GitHub Pages**, **Netlify Drop** (drag & drop the folder) or Cloudflare Pages.

## 3. Install on Android
Open the hosted URL in Chrome → ⋮ menu → **Install app / Add to Home screen**. It now opens full-screen like a normal app.
(Want a real .apk? Paste your hosted URL into https://www.pwabuilder.com → Android → Download.)

## How it works
- **Start screen**: type the Vatika name → opens that Vatika's dashboard + 12 forms.
- **Sections**: every form has *＋ Add section* / 🗑 (e.g. Vaibhavi-6, an extra Tejas table). LP Shop-Mitra offers all 4 of its tables.
- **Entries**: ＋ Add entry / Remove entry; Amount Due, Trainer Capital, Vaibhavi capital, Event Total and all TOTAL rows calculate live.
- **Photos**: 📷 on every entry (camera or gallery) – invoices, delivery proof, meeting/event photos. Uploaded to Drive; links go into a *Photos* column in the sheet.
- **Drive sync**: ~2.5 s after any edit, the app writes a Google Sheet per Vatika (`CBS Ledger - <Vatika>`, 12 tabs, real formulas) and a backup file inside the Drive folder **CBS Ledger App**. Tap the status chip to sync/retry. Log in on another phone with the same Google account → tap the chip → all Vatikas load.
- **⬇ Excel**: downloads the Vatika as .xlsx in the original layout.

## Notes
- Scope used is `drive.file`: the app only sees files it created itself.
- Google tokens last ~1 h; if a background save can't renew silently the chip turns red – tap it once.
- Edits are stored on-device first, so nothing is lost offline; they upload when you reconnect.
