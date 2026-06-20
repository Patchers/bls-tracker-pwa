# BLS Tracker — PWA Setup

This is a Progressive Web App. To get the "Install" prompt, it must be served over **HTTPS** (not opened as a local `file://` page — browsers block service workers and install prompts on file://).

## Fastest option: GitHub Pages (free)

1. Create a new GitHub repo (e.g. `bls-tracker`).
2. Upload all files from this folder, keeping the structure:
   ```
   index.html
   manifest.json
   sw.js
   icons/icon-192.png
   icons/icon-512.png
   icons/icon-maskable-512.png
   ```
3. In the repo: Settings → Pages → Source → select your main branch → Save.
4. GitHub gives you a URL like `https://yourusername.github.io/bls-tracker/`.
5. Open that URL on your phone in Chrome (Android) or Safari (iOS).
   - **Android/Chrome:** you'll see an "Install BLS Tracker" banner in-app, or use the browser menu → "Install app" / "Add to Home Screen."
   - **iOS/Safari:** tap the Share icon → "Add to Home Screen" (iOS doesn't support automatic install prompts, so the app shows manual instructions instead).

## Alternative: any static host

Netlify, Vercel, Cloudflare Pages, or your own server all work the same way — just upload these files as-is and visit the HTTPS URL. No build step needed.

## Notes

- All workout data is stored in the browser's `localStorage` on whichever device/browser you install it on. It does not sync between devices.
- If you update the app later, bump `CACHE_NAME` in `sw.js` (e.g. `bls-tracker-v2`) so the service worker refreshes cached files instead of serving stale ones.
