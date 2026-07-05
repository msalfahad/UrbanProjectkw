# Urban Projects — Website

A cinematic, bilingual (English + Arabic) one-page site for a construction & real-estate company.
Built as plain HTML/CSS/JS — no build step. Just open `index.html`.

> This folder is a standalone marketing site, separate from the `UrbanProjectsManager` Flutter
> app it currently lives alongside in this repo. It doesn't share build tooling or Firebase
> Hosting config with the app — copy the folder out if you want to host or version it on its own.

## How to preview
Double-click `index.html`, or drag it into any browser. Works on phone and desktop.

## File structure
```
index.html                 ← the whole site (HTML + CSS + JS in one file)
images/                    ← all photos (placeholders — swap with your own)
CLAUDE_CODE_PROMPT.md      ← paste this into Claude Code to finish/extend it
README.md                  ← this file
```

## Swapping in your real photos
Replace the files inside `images/` **keeping the same filenames**. That's it — the site
picks them up automatically. Recommended sizes:

| File | Used for | Best size |
|------|----------|-----------|
| hero.jpg | main top background | ~1920×1080 (landscape) |
| intro.jpg | statement section | ~1600×900 (landscape) |
| logo-fill.jpg | photo inside the big "URBAN" word | ~1600×600 |
| project-1…6.jpg | portfolio cards | portrait 4:5 (e.g. 1200×1500) |
| service-1…4.jpg | service hover backgrounds | landscape |
| gallery-1…4.jpg | scrolling strip | portrait 3:4 |

The logo files (`logo-transparent.png`, `logo-white.png`) are your uploaded Urban Projects logo.

## Editing text
All text is in `index.html`. English lines use normal text; Arabic lines sit right after
inside `<span class="ar">…</span>`. Edit either freely.

## Editing the services list
The "Our Services" overview is rendered from the `SERVICES` array in the `<script>` block of
`index.html`. Each entry has `en`, `ar`, `descEn`, `descAr`. Add/edit/reorder freely.

## Editing the Our Work gallery (categories, captions, carousels)
The category cards under "Our Work" are rendered from the `GALLERY` array in the `<script>`
block. Each category has an English + Arabic title and a `photos` list. Each photo has:

- `key`  — its image filename without extension (e.g. `finishing-1` → `images/finishing-1.jpg`);
  this is also what makes the photo swappable in admin mode.
- `img`  — the path shown on the page.
- `en` / `ar` — the caption shown on the photo, e.g. `العزل الحراري بأعلى جودة`.

If a category has more than one photo, the card automatically shows arrows, dots and thumbnails
so visitors can scroll through them. To add a photo, add another `{ key, img, en, ar }` entry and
drop the matching file into `images/`. To add a whole new category, copy a `{ ... photos:[...] }`
block.

## Admin — upload & publish photos yourself
Every photo on the site can be swapped from your browser, no code needed.

1. **Open admin mode:** add `?admin` to the site URL, e.g.
   `https://msalfahad.github.io/UrbanProjectkw/?admin`
2. **Swap a photo:** every photo gets a dashed gold outline. Click one, pick an image from your
   device — it's resized automatically and previews instantly. This preview is saved **in your
   browser only** (great for experimenting; visitors don't see it yet).
3. **Publish for everyone:** paste a GitHub token into the admin bar and press **Publish to
   website**. Your changed photos are committed to the repo and go live in ~1–2 minutes.
   - Create the token at **github.com → Settings → Developer settings → Fine-grained tokens →
     Generate new token**. Give it access to **only** the `UrbanProjectkw` repo, with
     **Repository permissions → Contents → Read and write**. Paste it once; it's stored only in
     your browser.
4. **Reset** removes your local changes; **Exit** leaves admin mode.

### Adding new photos yourself (with names & captions)
In admin mode each category card has a **“＋ Add photo”** button:

1. Click it, pick an image, and fill in **Photo name**, **English caption**, and **Arabic caption**.
2. The photo is added to that category's carousel instantly (preview on your device).
3. Use **🗑 Delete current** to remove the photo currently shown in a card.
4. Press **Publish** — your new/changed images are committed to `images/`, and the whole
   gallery (categories, photos, captions, order) is saved to `content/gallery.json`. The live
   site reads that file, so everyone sees your additions after the ~1–2 minute rebuild.

You never need to touch code to add photos — the built-in `GALLERY` list is only the starting
point; once `content/gallery.json` exists it takes over. Each photo is its own file in `images/`,
so swapping or adding one never affects the others.

## Deploying to Firebase Hosting
This folder is wired up as a second Firebase Hosting site (target `marketing`), separate from
the Flutter app's site (target `app`), via `firebase.json` and `.firebaserc` at the repo root.
One-time setup (needs a machine with Firebase CLI + `firebase login`, which this sandbox doesn't have):

```bash
npm install -g firebase-tools
firebase login
firebase hosting:sites:create urbanprojectskw --project urbanprojectsmanager
# targets are already mapped in .firebaserc, but if you change the site ID, re-run:
# firebase target:apply hosting marketing urbanprojectskw
firebase deploy --only hosting:marketing
```

After that first deploy, the site is live at `https://urbanprojectskw.web.app`. Future deploys
are just `firebase deploy --only hosting:marketing` — no build step needed, it's plain static files.

## Wiring up the forms
The contact form and newsletter form both submit to Formspree (https://formspree.io). Sign up,
create a form, and replace `YOUR_FORM_ID` (contact form) and `YOUR_NEWSLETTER_ID` (newsletter)
in `index.html` with your real Formspree endpoint IDs. No build step is required — Formspree
accepts the plain `fetch` POST already wired up in the script.

## About the Arabic
Per request, Arabic is set to run **left-to-right** while keeping letters correctly joined
and in the right order. To switch to standard right-to-left Arabic later, find `.ar{` near
the top of the `<style>` block and change `direction:ltr` to `direction:rtl`.

## Brand colors
- Gold `#E6A85B`  · Charcoal `#0E0E10`  · Cream `#F5F1EA`
