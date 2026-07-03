# Arish AI — Website

## ⚠️ Read this before uploading to GitHub

This zip must be **unzipped first**. Then, when uploading to GitHub, you must drag in the **contents** of the unzipped folder — not the folder itself.

After unzipping, you should see these items:

```
index.html
assets/          (a folder)
.nojekyll        (an empty file — may be hidden by your OS, that's normal)
README.md
```

### ✅ Correct upload
On your GitHub repo page → **Add file → Upload files** → drag in `index.html`, `assets`, `.nojekyll`, and `README.md` **individually**, so they land at the top level (root) of the repo:

```
your-repo/
├── index.html
├── assets/
├── .nojekyll
└── README.md
```

### ❌ Wrong — the #1 cause of broken images/videos
Dragging the whole unzipped folder in as one item, which nests everything one level too deep:

```
your-repo/
└── arish-ai-website/        ← wrong, extra folder
    ├── index.html
    ├── assets/
    └── ...
```

If `index.html` is not directly at the root of the repo, GitHub Pages cannot find your assets, and every image/video will 404 — this is almost always the cause when a GitHub Pages site shows a blank page with broken images.

**After uploading, check your repo's file list on github.com.** You should see `index.html` and `assets` sitting side by side at the top — not inside another folder.

---

## Deploying with GitHub Pages

1. Create a repository on GitHub (e.g. `arish-ai-website`), keep it **Public**.
2. Upload the four items above directly to the repo root (see correct method above).
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, select **Deploy from a branch** (not "GitHub Actions" — that requires extra setup and is more failure-prone for a simple static site).
5. Under **Branch**, choose `main` and `/ (root)`, then **Save**.
6. Wait 1–2 minutes, then refresh the Pages settings page — your live URL will appear:
   ```
   https://<your-username>.github.io/<your-repo>/
   ```

## Verifying it worked

Open the live URL and hard-refresh (`Ctrl+Shift+R` / `Cmd+Shift+R`). Check:
- The 6-card "AI in Action" carousel is auto-advancing with real images
- The product demo video plays
- All 6 sector tabs (Automobile, Industrial, Retail, Healthcare, Hospitals, Banking) switch correctly

If anything still 404s, open DevTools (F12) → **Network** tab → reload, and check the exact URL of the failing request — that tells you immediately whether it's a path/case mismatch or a missing file.

## Local preview before pushing (optional but recommended)

Don't just double-click `index.html` — video playback is unreliable when opened this way in most browsers (a browser limitation, not a bug). Instead, from this folder run:

```bash
npx serve .
```

and open the localhost link it prints. That's an accurate preview of what GitHub Pages will show.

## What's inside

- `index.html` — the entire site: structure, styles, and scripts in one file
- `assets/` — 6 carousel images, 4 demo videos, 4 video poster thumbnails
- `.nojekyll` — tells GitHub Pages to skip Jekyll processing, which can otherwise interfere with plain static sites
- This `README.md`

## Notes on functionality

- The enquiry chatbot sends messages via `mailto:` — it opens the visitor's own email app, pre-addressed to `contact@arishai.co.in`. There's no backend, so nothing sends silently.
- The cookie banner stores a preference cookie in the visitor's browser. No analytics are wired up yet, so nothing is tracked even after consent.
