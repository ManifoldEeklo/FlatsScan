# FastScan

Scan paper documents with your phone, flatten and clean them up, combine the pages into one PDF and send it to yourself. FastScan is an installable web app (PWA) with no build step and no server: everything runs in the browser.

## Project layout

```
public/                  the app (this folder is what gets deployed)
  index.html             the whole app
  manifest.webmanifest   install name, colors, icons
  sw.js                  service worker for offline use
  icon-*.png             app icons
vercel.json              Vercel settings
.github/workflows/       GitHub Pages deploy
```

## 1. Put it on GitHub

Create an empty repository on github.com (for example `fastscan`), then run this from this folder:

```bash
git init
git add .
git commit -m "FastScan"
git branch -M main
git remote add origin https://github.com/YOUR-NAME/fastscan.git
git push -u origin main
```

## 2a. Deploy with GitHub Pages

1. In the repository, open **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **GitHub Actions**.
3. Push to `main`, or run the workflow from the **Actions** tab.

After about a minute the app is live at `https://YOUR-NAME.github.io/fastscan/`. Every push to `main` redeploys it.

## 2b. Deploy with Vercel

1. Go to https://vercel.com/new and import the GitHub repository.
2. Leave the settings as they are: `vercel.json` already tells Vercel to serve the `public` folder with no build.
3. Click **Deploy**.

The app is live at `https://fastscan-xxxx.vercel.app`. Every push to `main` redeploys it, and pull requests get preview links.

From the command line instead: `npx vercel` for a preview and `npx vercel --prod` for the live site.

## 3. Install on your phone

Open the live link on your phone:

- **Android (Chrome):** menu → **Install app** (or **Add to Home screen**).
- **iPhone (Safari):** Share → **Add to Home Screen**.

The camera only works over HTTPS, which both GitHub Pages and Vercel provide.

## Updating the app

1. Edit the files in `public/`.
2. Raise the cache name at the top of `public/sw.js` (for example `fastscan-v3` → `fastscan-v4`) so installed copies pick up the new version.
3. Commit and push.

## Test locally

```bash
npx serve public
```

Open the address it prints. On `localhost` the camera works without HTTPS.
