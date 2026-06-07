# lantingy.github.io

Personal academic homepage for **Lanting Yang, PhD, MPH** — pharmacoepidemiology, environmental health, and real-world evidence. Live at <https://lantingy.github.io/>.

A static site (no build step, no framework). Just open `index.html` in a browser to preview locally.

## Files

| File | What it is |
|---|---|
| `index.html` | All page content + the inline `<script>` for interactivity |
| `style.css` | All styling, including dark mode and responsive rules |
| `images/` | Photos (Joey gallery), the social-share image, favicon |
| `Lanting-Yang-CV.pdf` | CV linked from the Contact section |
| `robots.txt`, `sitemap.xml` | SEO / search-engine hints |

## Sections (in `index.html`)

About · My Research (with expandable publication abstracts) · Posts · Grants & Projects · Contact · Coffee, Cat & Notes (Joey carousel + Notes).

## Common edits

### Add a Joey photo
1. Drop the image in `images/` (e.g. `joey-7.jpg`).
2. Add one line to the `joeyPhotos` list near the bottom of `index.html`:
   ```js
   { src: 'images/joey-7.jpg', caption: 'Your caption' },
   ```
   The carousel and dots update automatically.

### Add a Note
Find `<h3 class="coffee-label">Recent Notes</h3>` and paste an `<article class="blog-card">` block inside `<div class="blog-grid">` (a copy-paste template is in an HTML comment right there). Delete the "Notes coming soon." line once you add one.

### Add a Post
Copy any `<div class="post-card-v2">` block in the Posts section and edit the logo, title, date, and detail text.

### Add a publication
In the relevant `<div class="pub-panel">`, copy a `<div class="pub-item">` block and edit the title, journal, DOI link, and abstract. Highlight key terms with `<span class="kw">…</span>`.

### Update the CV
Replace `Lanting-Yang-CV.pdf` with the new file (keep the same name so the Contact link keeps working).

### Update the social-share image
The image used for link previews is `images/og-image.png` (1200×630). Replace it and keep the same name.

## Privacy note for photos
Phone photos can carry EXIF metadata, including **GPS location**. Strip it before committing public images, e.g.:
```bash
python3 -c "from PIL import Image, ImageOps; \
p='images/joey-7.jpg'; img=ImageOps.exif_transpose(Image.open(p)); \
clean=Image.new(img.mode,img.size); clean.putdata(list(img.getdata())); \
clean.save(p,'JPEG',quality=92,optimize=True)"
```

## Deploy
GitHub Pages serves the `main` branch automatically. After changes:
```bash
git add -A
git commit -m "Update site"
git push
```
Changes go live at <https://lantingy.github.io/> within a minute or two.
