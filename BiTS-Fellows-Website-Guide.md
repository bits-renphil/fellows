# BiTS Fellows Website — Editor Guide

This guide explains how to add a new fellow, update an existing one, and publish changes to the website. No coding experience is required, but you will need access to two things:

- **GitHub** — `github.com/bits-renphil/fellows` (where files are stored)
- **Squarespace** — the BiTS website admin panel

---

## How the directory works

The fellows directory is a single block of HTML code pasted into a Squarespace page. The headshot images and PDF concept notes are stored in the GitHub repository and loaded from there. Every time you want the live website to reflect a change, you edit the HTML file in GitHub and paste the updated version into Squarespace.

There are three steps to any update:

1. Upload assets (headshot, PDF) to GitHub
2. Edit the HTML file in GitHub
3. Paste the updated HTML into Squarespace

---

## Step 1 — Prepare the headshot image

Squarespace loads images directly from GitHub, so large files will slow the page down noticeably.

**Requirements:**
- Format: JPEG (`.jpg`) — not PNG, not WebP
- Maximum width or height: 800 pixels
- File name: `firstname-lastname.jpg`, all lowercase, hyphen-separated (e.g. `roslyn-bill.jpg`)

**On a Mac**, you can resize an image using Preview:
1. Open the image in Preview
2. Go to **Tools → Adjust Size**
3. Set width or height to 800 px (whichever is larger), with "Scale proportionally" ticked
4. Go to **File → Export**, choose JPEG, quality around 75–80%, save

Aim for a file size under 200 KB. Portrait (square or near-square) crops work best — the grid crops to square automatically, centred near the top of the image.

---

## Step 2 — Upload assets to GitHub

Go to `github.com/bits-renphil/fellows`.

### Upload the headshot

1. Click into the **`headshots`** folder
2. Click **Add file → Upload files**
3. Drag your JPEG onto the page
4. Scroll down and click **Commit changes**

### Upload the concept note PDF

1. Go back to the repo root and click into the **`pdfs`** folder
2. Click **Add file → Upload files**
3. Drag the PDF onto the page — name it `firstname-lastname.pdf` (e.g. `roslyn-bill.pdf`)
4. Click **Commit changes**

GitHub takes about 5–10 minutes to make new files publicly accessible. You can check by opening:
```
https://bits-renphil.github.io/fellows/headshots/firstname-lastname.jpg
```
in your browser. If you see the image, it's live.

---

## Step 3 — Edit the HTML file

The file you need to edit is **`squarespace-embed.html`** in the root of the repository.

1. Click `squarespace-embed.html` in the repo
2. Click the **pencil icon** (Edit this file) in the top-right corner

The file contains one block of HTML per fellow, surrounded by a comment that names the person:

```html
<!-- Roslyn Bill -->
<article class="bits-fellows__card" data-programme="aria" data-year="2025">
  ...
</article>
```

### Adding a new fellow

Find a card for a fellow in the same programme (ARIA or SPRIND) and copy the entire block from `<!-- Name -->` down to and including `</article>`. Paste it immediately after the last fellow in that programme's section, then update every field (see the field reference below).

**Template to copy and fill in:**

```html
<!-- FULL NAME -->
<article class="bits-fellows__card" data-programme="PROGRAMME" data-year="YEAR">
  <div class="bits-fellows__card-top">
    <img src="https://bits-renphil.github.io/fellows/headshots/FILENAME.jpg" alt="FULL NAME" loading="lazy">
    <div>
      <h2 class="bits-fellows__name">FULL NAME</h2>
      <span class="bits-fellows__affiliation">INSTITUTION</span>
      <div class="bits-fellows__tags">
        <span class="bits-fellows__tag">ARIA or SPRIND</span>
        <span class="bits-fellows__tag">YEAR</span>
      </div>
    </div>
  </div>
  <div class="bits-fellows__card-body">
    <div class="bits-fellows__programme">PROGRAMME TITLE<span class="bits-fellows__programme-sub">: PROGRAMME SUBTITLE</span></div>
    <p class="bits-fellows__summary">One or two sentences describing the project.</p>
  </div>
  <div class="bits-fellows__card-footer">
    <a href="https://bits-renphil.github.io/fellows/pdfs/FILENAME.pdf" target="_blank">Concept Note</a>
    <span class="bits-fellows__sep">|</span>
    <button class="bits-fellows__bio-toggle">Bio</button>
  </div>
  <div class="bits-fellows__bio">
    <p>Biographical paragraph here.</p>
  </div>
</article>
```

### Field reference

| Field | What to put | Example |
|---|---|---|
| `data-programme` | Programme identifier, lowercase | `aria` or `sprind` |
| `data-year` | Cohort year | `2025` or `2026` |
| `FILENAME` | Lowercase hyphenated name, no spaces | `roslyn-bill` |
| `alt="..."` | Fellow's full name | `Roslyn Bill` |
| `bits-fellows__name` | Fellow's display name | `Roslyn Bill` |
| `bits-fellows__affiliation` | Institution or `Independent` | `Aston University` |
| `bits-fellows__tag` (×2) | Programme label and year | `ARIA`, `2025` |
| `bits-fellows__programme` | Programme name — bold part before the colon | `FLOWCODE` |
| `bits-fellows__programme-sub` | Subtitle after the colon (include the `: ` at the start) | `: Tuning CNS Fluid Logistics` |
| `bits-fellows__summary` | 1–2 sentence project description | — |
| PDF `href` | Full GitHub Pages URL to the PDF | `https://bits-renphil.github.io/fellows/pdfs/roslyn-bill.pdf` |
| `bits-fellows__bio` | Full biographical paragraph | — |

> **If there is no affiliation:** remove the `<span class="bits-fellows__affiliation">...</span>` line entirely.
>
> **If there is no concept note yet:** remove the `<a href="...">Concept Note</a>` and `<span class="bits-fellows__sep">|</span>` lines, leaving just the Bio button.
>
> **If the programme has no subtitle:** write just the programme name with no `<span>` tag: `<div class="bits-fellows__programme">Primordial Deep Tech</div>`

### Editing an existing fellow

Find the fellow's block using **Ctrl+F / Cmd+F** and search their name. Make your changes in place. Be careful to keep the opening and closing tags intact — do not delete a `<` or `>` by accident.

---

## Step 4 — Save the file in GitHub

When you are done editing:

1. Scroll to the bottom of the GitHub editor
2. Leave the commit message as-is or write a short note (e.g. "Add Jerome Unidad")
3. Click **Commit changes**

---

## Step 5 — Paste into Squarespace

The HTML file in GitHub is the source of truth, but the website reads a copy pasted into a Squarespace code block. You need to update that copy every time you commit a change.

1. Go to the GitHub file view (`squarespace-embed.html`), click the **Raw** button
2. Select all the text (Ctrl+A / Cmd+A) and copy it (Ctrl+C / Cmd+C)
3. Log in to Squarespace and navigate to the Fellows page
4. Click **Edit** on the page, then click on the code block containing the fellows directory
5. Select all the existing content in the code block and delete it
6. Paste (Ctrl+V / Cmd+V) the new content
7. Click **Save**, then **Publish**

The changes will be live immediately.

---

## Quick checklist for adding a new fellow

- [ ] Headshot resized to max 800 px and saved as JPEG
- [ ] Headshot uploaded to `headshots/` in GitHub repo
- [ ] PDF uploaded to `pdfs/` in GitHub repo
- [ ] New card block added to `squarespace-embed.html` with all fields filled in
- [ ] `data-programme` matches the correct filter (`aria` / `sprind`)
- [ ] `data-year` set to the correct cohort year
- [ ] Image URL and PDF URL both use `bits-renphil.github.io/fellows/...`
- [ ] Changes committed in GitHub
- [ ] Updated HTML pasted into Squarespace code block and published

---

## Common mistakes

**The headshot doesn't appear.**
Check that the filename in the HTML matches exactly what was uploaded to GitHub (including the extension — `.jpg` not `.jpeg` or `.png`). Also wait 5–10 minutes after upload for GitHub Pages to propagate.

**The filter buttons don't show this fellow.**
Check the `data-programme` attribute. It must be exactly `aria` or `sprind` (lowercase). If a new programme is added in the future, contact the person who manages the code.

**The page looks broken after editing.**
You may have accidentally deleted a tag. In the GitHub editor, press **Cancel** to discard your changes, or use the **History** tab on the file to restore a previous version.

**The bio doesn't expand when clicked.**
The bio button and the bio text must both be present. Check that neither the `<button class="bits-fellows__bio-toggle">` nor the `<div class="bits-fellows__bio">` block was accidentally removed.
