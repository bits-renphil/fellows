# BiTS Fellows Website — Editor Guide

This guide explains how to add a new fellow, update an existing profile, and publish changes to the website. No coding experience is required.

You will need access to two things:

- **Google Sheet** — the fellows data spreadsheet (ask a team member for the link if you don't have it)
- **GitHub** — `github.com/bits-renphil/fellows` (where headshots and PDFs are stored)

---

## How the directory works

The fellows directory fetches all profile data live from a Google Sheet every time the page loads. This means:

- **To change any text** (names, affiliations, bios, summaries) → edit the Google Sheet
- **To change a headshot or concept note** → upload the file to GitHub, then update the URL in the Google Sheet
- **You do not need to touch the HTML or Squarespace** for routine updates

The page auto-refreshes its data from the sheet — changes are live within seconds of saving.

---

## Editing the Google Sheet

Open the spreadsheet. Each row is one fellow. The columns are:

| Column | What goes here | Example |
|---|---|---|
| **Name** | Fellow's full display name | `Roslyn Bill` |
| **Affiliation** | Institution or `Independent` | `Aston University` |
| **Cohort** | Programme identifier — must be one of: `aria`, `sprind`, `americas`, `japan` (lowercase) | `aria` |
| **Year** | Cohort year | `2025` |
| **Program Title** | Bold part of the programme label | `FLOWCODE` |
| **Program Subtitle** | The part after the colon (no colon needed) | `Tuning CNS Fluid Logistics` |
| **Summary** | 1–2 sentence project description; start with an active verb | `Develops a platform to…` |
| **Bio** | Full biographical paragraph | — |
| **Headshot URL** | Full URL to the image on GitHub Pages | `https://bits-renphil.github.io/fellows/headshots/roslyn-bill.jpg` |
| **Concept Note URL** | Full URL to the PDF on GitHub Pages, OR the text `on request`, OR leave blank | `https://bits-renphil.github.io/fellows/pdfs/roslyn-bill.pdf` |

> **Concept Note URL rules:**
> - If the PDF is publicly available: paste the full `https://bits-renphil.github.io/...` URL
> - If available on request only: type `on request`
> - If there is no concept note: leave the cell blank

Save the sheet after editing — changes go live immediately.

---

## Uploading a headshot to GitHub

Headshot images must be uploaded to the `headshots` folder in the GitHub repository.

### Before uploading — prepare the image

- **Format:** JPEG (`.jpg`) — not PNG, not WebP
- **Maximum dimension:** 800 px on the longest side
- **File name:** `firstname-lastname.jpg`, all lowercase, hyphens instead of spaces (e.g. `roslyn-bill.jpg`)
- **Target file size:** under 200 KB

**On a Mac**, resize with Preview:
1. Open the image in Preview
2. Go to **Tools → Adjust Size**
3. Set the width or height to 800 px (whichever is larger), with "Scale proportionally" ticked
4. Go to **File → Export**, choose JPEG, quality ~75–80%, save

The grid crops headshots to a circle. Portrait shots work best — the crop centres near the top of the image (roughly face height).

### Upload to GitHub

1. Go to `github.com/bits-renphil/fellows`
2. Click into the **`headshots`** folder
3. Click **Add file → Upload files**
4. Drag your JPEG onto the page
5. Click **Commit changes**

GitHub Pages takes **5–10 minutes** to make new files publicly accessible. You can verify by opening:
```
https://bits-renphil.github.io/fellows/headshots/firstname-lastname.jpg
```
in your browser. If you see the image, it's live.

6. Copy that URL and paste it into the **Headshot URL** column in the Google Sheet.

---

## Uploading a concept note PDF to GitHub

1. Go to `github.com/bits-renphil/fellows`
2. Click into the **`pdfs`** folder
3. Click **Add file → Upload files**
4. Drag the PDF onto the page — name it `firstname-lastname.pdf` (e.g. `roslyn-bill.pdf`)
5. Click **Commit changes**

Wait 5–10 minutes, then verify:
```
https://bits-renphil.github.io/fellows/pdfs/firstname-lastname.pdf
```

6. Copy that URL and paste it into the **Concept Note URL** column in the Google Sheet.

---

## Adding a new fellow — checklist

- [ ] Headshot prepared: JPEG, max 800 px, under 200 KB, named `firstname-lastname.jpg`
- [ ] Headshot uploaded to `headshots/` in the GitHub repo
- [ ] Headshot URL verified in browser, then pasted into the Google Sheet
- [ ] PDF uploaded to `pdfs/` in the GitHub repo (if applicable)
- [ ] PDF URL pasted into the Google Sheet (or `on request`, or left blank)
- [ ] New row added to the Google Sheet with all columns filled in
- [ ] `Cohort` is one of: `aria` / `sprind` / `americas` / `japan` (lowercase)
- [ ] `Year` is set to the correct cohort year
- [ ] `Summary` starts with an active verb (e.g. "Develops…", "Builds…", "Investigates…")

---

## Editing an existing fellow

Find their row in the Google Sheet, make your changes, and save. No other steps needed.

---

## Common mistakes

**The headshot doesn't appear.**
Check that the URL in the Google Sheet matches the filename exactly (including the `.jpg` extension). Also wait 5–10 minutes after upload for GitHub Pages to propagate.

**The filter buttons don't show this fellow.**
Check the `Cohort` column. It must be exactly `aria`, `sprind`, `americas`, or `japan` — lowercase, no spaces.

**The concept note link doesn't appear.**
The URL must start with `https://`. If it starts with `http://` or has a typo, the link won't render. Check the cell value carefully.

**The bio toggle doesn't work.**
Make sure the Bio column is not empty. Even a single space will cause it to appear blank when expanded.

---

## Making design changes (advanced)

The visual layout, colours, and filters are controlled by the HTML/CSS file in the GitHub repo (`squarespace-embed.html`). You should not need to change this for routine content updates. If design changes are needed, contact the person managing the code — changes to the HTML file do require pasting the updated version into the Squarespace code block.
