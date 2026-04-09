# ÁUREA NYC Fashion Show Dashboard

Production dashboard for organizing ÁUREA Argentina's fashion show in New York City. A real-time, mobile-first web tool built for a small creative team to coordinate every detail — from the collection and moodboard to the budget and soundtrack.

**Live:** [nyfashionshow-aurea-dashboard.netlify.app](https://nyfashionshow-aurea-dashboard.netlify.app/)

---

## About

[ÁUREA Argentina](https://www.aureaargentina.com) ([@aurea.arg](https://instagram.com/aurea.arg)) is a high-end upcycling fashion brand. This dashboard was built so the designer could centralize all production logistics for her first NYC runway show — accessible from any device, with real-time sync and zero setup required from the team.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Single-file HTML5 + vanilla CSS3 + vanilla JavaScript |
| Database | Firebase Firestore (real-time NoSQL) |
| Storage | Firebase Storage (images) |
| Hosting | Netlify (static deploy) |
| Fonts | Bebas Neue · DM Sans · Cormorant Garamond |

### Why this stack?

- **Single-file HTML** — No framework, no bundler, no build step. Easy to maintain and deploy (drag & drop on Netlify). Perfectly suited for a personal/small-team tool.
- **Firebase** — Free tier covers all usage. Firestore provides real-time sync across devices with no custom server required.
- **Local Firebase SDK** — The SDK files (`/js/`) are bundled locally instead of loaded from a CDN to avoid intermittent network/browser issues encountered during development.
- **Netlify** — Instant static deploy with free HTTPS and custom subdomains.

## Features

### 10 Sections

| # | Section | Description |
|---|---------|-------------|
| 1 | **General Info** | Show details — name, date, venue, schedule, number of looks, duration. Inline editable with auto-save. |
| 2 | **Moodboard** | Visual boards with uploaded images, tags, inspiration notes, and highlighted details. Fullscreen view + lightbox. Auto image compression (1200px max, JPEG 70%). |
| 3 | **Collection** | Garment grid with photo, name, category, notes, and ready-status checkbox. Categories: Top, Bottom, Set, Accessory, Shoes, Other. Downloadable as PDF. |
| 4 | **Timeline** | Chronological schedule with auto-sorting by date, visual dot-and-line connectors. Downloadable as PDF. |
| 5 | **Team** | Production contacts — role, name, phone, email, Instagram, notes. Downloadable as PDF. |
| 6 | **Useful Links** | Link repository organized by type (Google Drive, Doc, Spreadsheet, Instagram, Web, Other) with visual icons. |
| 7 | **Music / Soundtrack** | Tracks with artist, mood notes, and direct links to Spotify, YouTube, SoundCloud, or Apple Music. Platform-aware icons. Downloadable as PDF. |
| 8 | **Budget** | Categorized expenses with inline input, auto-calculated subtotals per category, and a running grand total. Collapsible categories. |
| 9 | **Creative Process** | Free-form text editor with serif typography (Cormorant Garamond) for writing the show narrative, look order, and concepts. Auto-save with visual confirmation. |
| 10 | **Notes** | Quick timestamped notes in reverse chronological order. |

### Cross-Cutting Features

- **ES/EN Translation** — Language toggle in the header. All UI labels, section titles, and downloaded PDFs respect the selected language.
- **PDF Export** — One-click PDF generation for Collection, Timeline, Team, and Music sections, branded with the ÁUREA logo and show details.
- **Export / Import** — Full JSON backup and restore of all dashboard data.
- **Real-Time Sync** — Dual storage: localStorage for instant load + Firestore for cross-device sync. 1-second debounce to avoid excessive writes.

## Visual Identity

| Role | Color | Hex |
|------|-------|-----|
| Background | Warm cream | `#F5F0E8` |
| Cards | White | `#FFFFFF` |
| Primary / CTA | ÁUREA Orange | `#E85D26` |
| Accent | Organic green | `#7BA355` |
| Dark green | Tags, roles | `#4B6B30` |
| Main text | Dark brown | `#2A2520` |
| Secondary text | Medium brown | `#7A7060` |
| Borders | Beige | `#DDD5C8` |

**Typography:** Bebas Neue (headings) · DM Sans (body/UI) · Cormorant Garamond (creative editor)

## Project Structure

```
aurea-dashboard/
├── index.html                        # Complete app (HTML + CSS + JS)
├── js/
│   ├── firebase-app-compat.js        # Firebase App SDK v9.23.0
│   ├── firebase-firestore-compat.js  # Firestore SDK
│   └── firebase-storage-compat.js    # Storage SDK
└── README.md
```

## Deployment

### Option 1: Netlify Drop (easiest)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop the project folder (with `index.html` and `/js/`)
3. Netlify generates a URL automatically

### Option 2: Netlify CLI

```bash
npm install -g netlify-cli
netlify deploy --prod --dir .
```

## Usage

1. Open the dashboard URL from any device
2. Add information to any section — data auto-saves
3. Changes sync in real time across all devices via Firebase
4. Download sections as PDF via the "⬇ PDF" button
5. Toggle language with the EN/ES button in the header
6. Back up data anytime with the Export button (downloads JSON)

## Known Limitations

- Firebase security rules are in test mode (expire after 30 days) — update them for long-term use
- No user authentication — anyone with the URL can edit (by design, for personal use)
- Images are stored as base64 in Firestore (1 MB document limit) — for heavy image use, consider migrating to Firebase Storage URLs
- PDF generation relies on the browser's native print dialog

## Firebase Configuration

- **Project ID:** `nyfashionshow-aurea-dashboard`
- **Database:** Firestore `(default)` — test mode
- **Storage bucket:** `nyfashionshow-aurea-dashboard.firebasestorage.app`
- **Region:** US-CENTRAL1
- **Cost:** Free tier (5 GB storage, 50K reads/day, 20K writes/day, 1 GB download/day)

## Credits

- **Dashboard by:** Emi Sebergamin — Product & Project Manager ([@emilsebergamin](https://instagram.com/emilsebergamin))
- **Brand:** ÁUREA Argentina — Manuela Mendari ([@aurea.arg](https://instagram.com/aurea.arg))
- **Built with:** Claude AI (Anthropic), Claude Code, Netlify, Firebase

## License

Private project. All ÁUREA brand rights belong to ÁUREA Argentina.
