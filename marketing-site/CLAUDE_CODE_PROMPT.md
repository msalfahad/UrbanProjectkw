# Prompt for Claude Code — Urban Projects website

Paste everything below the line into Claude Code, inside the project folder that contains `index.html` and the `images/` folder.

---

I have a working cinematic bilingual (English + Arabic) one-page website for a construction & real-estate company called **Urban Projects / المشاريع الحضرية**. The files are `index.html` and an `images/` folder. It already works — I want you to refine and extend it, keeping the existing look and feel exactly.

**Do not change:**
- The brand gold `#E6A85B`, charcoal `#0E0E10`, cream `#F5F1EA` palette.
- The cinematic parallax, scroll reveals, text-mask wipes, and the image-filled "URBAN" word.
- The logo (`images/logo-transparent.png` on dark, `images/logo-white.png` on light).
- The bilingual pattern: every headline/key line appears in English **and** Arabic. Arabic uses `class="ar"` with `direction:ltr; unicode-bidi:plaintext` so letters stay correctly joined and in order while the block aligns left. Keep that convention on any new text.
- Mobile-first responsiveness and `prefers-reduced-motion` support.

**Please do the following:**
1. Wire the contact form and newsletter form to a real backend or service (e.g. Formspree, or a simple `/api/contact` endpoint). Keep the existing success messages.
2. Replace the placeholder images in `images/` (same filenames) with the real project photos I will drop in — don't rename them, just make sure sizes/aspect-ratios still look good and add `loading="lazy"` where sensible.
3. Add real page `<title>`, meta description, Open Graph tags, and a favicon from the logo.
4. Split the projects into a small data array in the JS and render the cards from it, so I can add/remove projects by editing one list. Keep the bilingual fields (english title + arabic title + tag).
5. Add basic SEO + accessibility polish: alt text on all real images, skip-to-content link, and check color contrast.
6. Keep it a static site (plain HTML/CSS/JS, no build step) unless a form backend requires one.

Confirm the plan briefly, then make the changes. After each change, keep the site openable by just double-clicking `index.html`.

---

### Notes on the Arabic
Per the owner's request, Arabic text is set to flow left-to-right (`direction:ltr`) while `unicode-bidi:plaintext` preserves correct Arabic letter joining and word order. If you add Arabic, copy an existing `.ar` element as a template. If the owner later wants standard right-to-left Arabic, change `.ar { direction:ltr }` to `direction:rtl` in the CSS `:root`/`.ar` rule — that single edit flips all Arabic site-wide.

### Image filenames (keep these names when swapping in real photos)
- `hero.jpg` — main hero background (wide, ~1920×1080)
- `intro.jpg` — statement section background
- `logo-fill.jpg` — the photo shown inside the big "URBAN" letters
- `project-1.jpg` … `project-6.jpg` — portfolio cards (portrait 4:5)
- `service-1.jpg` … `service-4.jpg` — service row hover backgrounds
- `gallery-1.jpg` … `gallery-4.jpg` — horizontal gallery strip (portrait 3:4)
