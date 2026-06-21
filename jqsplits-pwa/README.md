# JQSplits — PWA Setup

A 7-day training split tracker: Push → Pull → Legs → Recovery → Upper Hypertrophy → Full Body Conditioning → Rest. This is a Progressive Web App, so it must be served over **HTTPS** to offer the "Install" prompt — opening the file directly (`file://`) won't work.

## Fastest option: GitHub Pages (free)

1. Create a new GitHub repo (e.g. `jqsplits`).
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
4. GitHub gives you a URL like `https://yourusername.github.io/jqsplits/`.
5. Open that URL on your phone:
   - **Android/Chrome:** an "Install JQSplits" banner appears in-app, or use the browser menu → "Install app."
   - **iOS/Safari:** tap Share → "Add to Home Screen" (manual instructions shown in-app since iOS has no automatic prompt).

## Alternative: any static host

Netlify, Vercel, Cloudflare Pages, or your own server work the same way — upload as-is, visit the HTTPS URL.

## How progression works

This program progresses **reps before weight**, matching the written plan:
- If you didn't hit the bottom of an exercise's rep range last week, it suggests repeating the same weight.
- If you're within the rep range but below the top, it suggests adding 1–2 reps at the same weight.
- Once you hit the top of the range, it suggests a weight increase (using your % in Settings) and resets the rep target back to the bottom of the range.
- Bodyweight moves (push-ups, pull-ups, plank) track reps/seconds only — no weight suggestion.

Walks, treadmill sessions, stretching, and meal-prep style items are simple tap-to-check checklist rows, not logged sets.

## Notes

- Data is stored in the browser's `localStorage` on the installed device only — no cross-device sync.
- To push an update later, bump `CACHE_NAME` in `sw.js` (e.g. `jqsplits-v2`) so the service worker doesn't serve stale cached files.
