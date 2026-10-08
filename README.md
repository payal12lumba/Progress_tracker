# Placement Prep Tracker (installable app)

Files in this folder:

```
index.html              the app
manifest.webmanifest   makes it installable (name, icon, colours)
sw.js                  service worker: lets it open offline
icons/                 app icons
.nojekyll              tells GitHub Pages to serve files as they are
README.md              this guide
```

---

## Part 1 — Put it on GitHub

### 1. Create a GitHub account
Go to https://github.com/signup and sign up (free).

### 2. Create a repository
1. Click the **+** (top right) → **New repository**.
2. Repository name: `placement-tracker`
3. Choose **Public** (GitHub Pages is free for public repos).
4. Tick **Add a README file** (optional, we will overwrite it).
5. Click **Create repository**.

### 3. Upload the files
**Option A — from the browser (easiest)**
1. Open your repository. Click **Add file → Upload files**.
2. Drag in `index.html`, `manifest.webmanifest`, `sw.js`, `README.md` and the whole `icons` folder.
3. Scroll down, type a commit message such as `first version`, click **Commit changes**.
4. Add the empty `.nojekyll` file: click **Add file → Create new file**, name it exactly `.nojekyll`, leave the content empty, click **Commit changes**.
   (Some computers hide files that start with a dot, so creating it here is safer.)

**Option B — with Git on your computer**
```bash
cd progress-tracker
git init
git add .
git commit -m "first version"
git branch -M main
git remote add origin https://github.com/<your-username>/placement-tracker.git
git push -u origin main
```

### 4. Turn on GitHub Pages
1. In the repo, click **Settings** → **Pages** (left sidebar).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Under **Branch**, pick **main** and **/ (root)**, then click **Save**.
4. Wait 1–3 minutes, then refresh the Pages settings page. It will show your link:
   `https://<your-username>.github.io/placement-tracker/`
5. Open that link in your browser to check it works.

---

## Part 2 — Install it on your phone (looks and opens like an app)

The link must be opened in **Chrome (Android)** or **Safari (iPhone)**.

**Android (Chrome)**
1. Open `https://<your-username>.github.io/placement-tracker/`.
2. Tap the **⋮** menu (top right) → **Install app** (or **Add to Home screen**).
3. Tap **Install**. An icon named "Placement" appears on your home screen.
4. Open it from the icon. It runs full screen, without the browser bar.

**iPhone (Safari)**
1. Open the link in **Safari** (not Chrome).
2. Tap the **Share** button → **Add to Home Screen** → **Add**.

**Computer (Chrome or Edge)**
- Click the install icon at the right of the address bar, then **Install**.

---

## Part 3 — Updating the app later

1. Edit the files (for example, change the plan data in `index.html`).
2. Open `sw.js` and change `const CACHE_VERSION = 'v2';` to `'v3'`, then commit. This tells phones to fetch the new version.
3. Upload the changed files to GitHub (Add file → Upload files, or `git push`), or edit them directly on GitHub.
4. Close and reopen the app on your phone. If it does not update, open it once in Chrome, or uninstall and reinstall.

---

## Important notes

- **Progress is stored on each device/browser.** It is not synced between your phone and computer.
  To move progress, open the app → **Export** (saves a JSON file) → on the other device **Import** that file.
  Export regularly, because clearing browser data deletes progress.
- The GitHub link is public, but nobody else can see your progress. It is stored only in the browser.
- Changing a date in the spreadsheet does **not** reset progress (statuses are matched on area, topic and resource).

## Troubleshooting

| Problem | Fix |
|---|---|
| Pages link shows 404 | Check Settings → Pages: branch `main`, folder `/ (root)`. Wait 3 minutes. Make sure `index.html` is in the top level of the repo, not inside a sub-folder. |
| "Install app" option missing | Open the link in Chrome (Android) or Safari (iPhone). Make sure you are on the `https://` address. |
| Old version still showing | Bump `CACHE_VERSION` in `sw.js`, re-upload, then reopen the app. |
| Icon looks old | Remove the home-screen icon, then add it again. |
| Progress disappeared | It is per browser. Use Import on the device where you exported it. |

---

## Optional — a real Android .apk / Play Store app later

This folder is a web app that installs like an app. To turn it into a real `.apk` or `.aab`,
open your Pages link at https://www.pwabuilder.com, enter the URL, and use **Package for stores → Android**.
It produces an Android package from the same files. You don't need to change the code.
