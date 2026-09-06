# Deutsch Pang — A1 → C2

A browser-based German vocabulary game (Pang/balloon-shooter style). Single-page,
no build step, no server required. Progress is saved locally per-device
(`localStorage`), with a simple export/import code to move a save between devices.

## Play it locally

Just open `index.html` in a browser — no install needed. Note: some browsers
block `localStorage`/audio on `file://` URLs, so for the smoothest local test,
serve it instead of double-clicking the file:

```bash
cd deutsch-pang
python3 -m http.server 8000
# then open http://localhost:8000
```

## 1. Put it on GitHub

From inside this folder:

```bash
git init
git add .
git commit -m "Deutsch Pang: initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/deutsch-pang.git
git push -u origin main
```

(Create the empty repo on github.com first — no README/license selected there,
so it doesn't conflict with the one already in this folder.)

### Turn on GitHub Pages (free hosting + HTTPS)

1. On the repo page: **Settings → Pages**.
2. Under "Build and deployment", set **Source** to `Deploy from a branch`.
3. Branch: `main`, folder: `/ (root)`. Save.
4. After a minute your game is live at:
   `https://<your-username>.github.io/deutsch-pang/`

You now have a shareable link and an HTTPS URL, which the Play Store step below requires.

## 2. Publish to Google Play

An HTML5 game like this gets published on Google Play as a **TWA (Trusted Web
Activity)** — a thin native wrapper that opens your hosted site full-screen,
with no browser chrome. It's the standard way to ship a PWA to Play.

**What you need first:**
- The game hosted on HTTPS (done via GitHub Pages above).
- A [Google Play Console](https://play.google.com/console) developer account
  (one-time $25 fee, real name/organization + identity verification).
- A privacy policy page (a public URL — a simple page or GitHub Pages doc
  saying what data you collect; this one only stores progress locally, so it
  can be short) — required by Play Console even for simple games.

**Steps (no Android Studio needed):**

1. Go to **[pwabuilder.com](https://www.pwabuilder.com)**.
2. Enter your GitHub Pages URL and let it scan the site. It will read
   `manifest.json` (already included in this repo) and report PWA readiness.
3. Click **Package for stores → Android**. PWABuilder generates a signed
   Android App Bundle (`.aab`) that wraps your site as a TWA, using the
   included icons and manifest.
4. It will also generate an `assetlinks.json` file — upload this to
   `https://<your-username>.github.io/deutsch-pang/.well-known/assetlinks.json`
   (create a `.well-known` folder in the repo with this file, commit, push).
   This proves you own both the app and the website, so the TWA opens
   without a browser address bar.
5. In Play Console: **Create app** → fill store listing (title, description,
   screenshots — you can screenshot the game running in a browser), set
   content rating questionnaire, privacy policy URL, and target audience.
6. Upload the `.aab` from step 3 under **Production → Create release** (or
   start with **Internal testing** to try it privately first — recommended).
7. Submit for review. First-time app reviews typically take a few days.

**Alternative (if you prefer full control / Android Studio):** use
[Bubblewrap CLI](https://github.com/GoogleChromeLabs/bubblewrap) instead of
PWABuilder's web UI — same TWA approach, run locally.

## Project structure

```
deutsch-pang/
├── index.html          # the game (all HTML/CSS/JS in one file)
├── manifest.json        # PWA manifest (name, icons, colors)
├── service-worker.js     # basic offline caching
├── icons/                # app icons for the manifest / Play listing
└── README.md
```

## License

© 2026 Javed Ghafoor. All rights reserved. This project is **not** open
source — no one may copy, modify, or redistribute it without written
permission. See [LICENSE](LICENSE) for details, or contact
ghafoorjaved@gmail.com to request permission.
