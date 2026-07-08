<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1E3A5F,100:D4AF37&height=200&section=header&text=SK%20STARK&fontSize=60&fontColor=ffffff&fontAlignY=35&desc=Sri%20Kumar%20M%20%7C%20JOJO%20Digital&descAlignY=55&descSize=20&animation=fadeIn" width="100%"/>

<a href="https://srikumarm8248-droid.github.io"><img src="https://readme-typing-svg.demolab.com?font=Syne&size=22&duration=3000&pause=1000&color=D4AF37&center=true&vCenter=true&width=650&lines=Agentic+AI+Freelancer+%7C+Web+%26+App+Builder;NSS+Programme+Officer+%40+M.G.R.+College;JOJO+Digital+-+Hosur%2C+Tamil+Nadu;Python+%2B+React+Native+%2B+AI+Automation" alt="Typing SVG" /></a>

</div>

<br>

## About

This repository powers the **NSS Volunteer Digital ID & Registration System** for the
National Service Scheme unit at M.G.R. College, Hosur. A student fills out one form —
name, class, subject, contact details, Aadhaar, community, blood group, and a photo — and
the system handles everything else: a unique sequential volunteer ID, a designed front-and-back
ID card, a confirmation email, and a logged entry in the master register. No manual data
entry on the NSS office's side.

Built entirely on a zero-cost stack: **GitHub Pages** for hosting, **Google Apps Script**
for the backend, and a **Google Sheet** as the database. Nothing here needs a paid server,
a database subscription, or a domain.

## What's in this repo

| File | Purpose |
|---|---|
| `index.html` | The registration site — 3D scroll intro, the step-by-step wizard, client-side ID card rendering, and the success screen |
| `Code.gs` | Google Apps Script backend — assigns sequential volunteer IDs, writes to the Sheet, stores photos in Drive, and emails the finished ID card |
| `assets/nss-banner.svg`, `assets/status-badge.svg` | Animated SVG graphics used in this README |
| `README.md` | You're reading it |

> `Code.gs` is kept here for version history. The **live** copy that actually runs lives
> inside the Apps Script editor attached to the registration Google Sheet — that one needs
> the real Sheet ID and Drive folder IDs filled in, not this file.

## How it works

1. A visitor scrolls through a short animated intro, then lands on the registration wizard.
2. They fill in their details one step at a time — validated as they go, so mistakes get
   caught immediately instead of at the end.
3. For their photo, they choose either a live camera capture or a file upload.
4. On submit, the backend checks the 500-entry cap, validates every field server-side, and
   assigns the next volunteer ID in sequence: `C26UG111NSS001`, `C26UG111NSS002`, and so on.
5. The browser renders the front and back of the ID card — photo, name, role, batch, and a
   QR code — and produces both a PNG and a PDF.
6. The finished card is emailed to the student, a notification copy goes to the NSS office,
   and everything is logged in the Google Sheet.
7. The success screen shows a full summary of what was submitted, plus two manual backup
   options: open a pre-filled email to the office, or copy all the details to the clipboard.
8. Anyone who's already registered can retrieve their card again later using their
   volunteer ID or the email they registered with.

### Preview mode

If the Apps Script backend hasn't been deployed yet (i.e. `APPS_SCRIPT_URL` in `index.html`
is still a placeholder), the site doesn't fail — it switches into **preview mode**: a local,
clearly-labelled demo ID is assigned so you can test the full form, camera/upload flow, card
design, and downloads without anything being saved or emailed for real. A visible banner
always makes it obvious when you're in this mode.

## Design system — "Seva" (சேவை)

A palette built around NSS's own visual language — marigolds at camp inaugurations,
tree-planting drives, the rising-sun emblem — rather than a generic corporate look.

| Token | Hex | Used for |
|---|---|---|
| Indigo Dusk | `#1C2541` | Base background |
| Marigold | `#E8A33D` | Primary accent / calls to action |
| Banyan Green | `#4B6B53` | Success states, secondary accent |
| Parchment | `#EDE6D6` | Card text on dark surfaces |

Fonts: **Syne** (display), **Plus Jakarta Sans** (body), **JetBrains Mono** (ID numbers).

## Known limitations

- **`mailto:` links can't carry attachments** — the "Send my details to the NSS office"
  button on the success screen fills in text only. The photo and finished ID card only
  travel as real email attachments through the automatic backend email once it's deployed.
- **Some in-app browsers / preview sandboxes restrict downloads and email intents.** If a
  button doesn't do anything in an embedded preview, try the same page in a normal Chrome
  or Safari tab, or use the deployed GitHub Pages link below — the code has fallbacks for
  most restricted environments, but a handful of sandboxes disable these features entirely
  at the browser level.
- **The 500-entry cap and duplicate-email check both rely on a full sheet scan.** Fine at
  this scale; would need optimizing if this system were ever reused for a few thousand
  entries.

## Setup checklist

1. Create a Google Sheet with a tab named exactly `Registrations` — see the header row
   listed in the comment at the top of `Code.gs`.
2. Create two Drive folders (one for photos, one for finished cards) and grab their folder
   IDs from the URL.
3. Paste `Code.gs` into Extensions → Apps Script on that Sheet, and fill in `SHEET_ID`,
   `PHOTOS_FOLDER_ID`, `CARDS_FOLDER_ID`.
4. Deploy it as a Web App (Execute as: Me, Who has access: Anyone), and copy the deployment
   URL into `APPS_SCRIPT_URL` near the top of `index.html`.
5. Push everything to this repo's `main` branch — GitHub Pages serves it automatically.

## Live site

**[srikumarm8248-droid.github.io/NSS-Team-Registration](https://srikumarm8248-droid.github.io/NSS-Volunteer-Registration/)**

## Maintained by

NSS Unit, M.G.R. College, Hosur — Sri Kumar M, Programme Officer

<div align="center">
<sub>Not Me, But You</sub>
</div>
