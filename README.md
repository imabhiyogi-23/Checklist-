# Adinath Visuals — Shoot Checklist

A fully offline, mobile-first day-to-day equipment checklist for the **Jokumara** unit.
Browse the equipment catalog, add items to **Today's Bucket** (cart-style), tick off
**Pickup** and **Pack-up** for each item with timestamps, then export or share the
result as text, PDF, or straight to WhatsApp.

Everything runs client-side — no backend, no build step, no external API calls at
runtime. It works with the phone in airplane mode on set.

## Files

```
index.html      the entire app (HTML + CSS + JS, jsPDF embedded inline)
manifest.json   PWA manifest so it can be "Added to Home Screen" as a standalone app
sw.js           service worker that caches the app shell for offline install
icons/          app icons used by the manifest / home screen shortcut
```

## Deploy with GitHub Pages

1. Create a new GitHub repository (public or private with Pages enabled on your plan).
2. Upload all the files in this folder to the repo root, keeping the `icons/` folder
   structure intact. Easiest ways:
   - **GitHub web UI:** open the repo → *Add file* → *Upload files* → drag in
     `index.html`, `manifest.json`, `sw.js`, and the `icons` folder → Commit.
   - **Git command line**, from inside this folder:
     ```
     git init
     git add .
     git commit -m "Shoot checklist app"
     git branch -M main
     git remote add origin https://github.com/<your-username>/<repo-name>.git
     git push -u origin main
     ```
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`, branch
   `main`, folder `/ (root)`. Save.
5. GitHub will give you a URL like:
   `https://<your-username>.github.io/<repo-name>/`
   It can take a minute or two to go live the first time.
6. Open that URL on your phone → browser menu → **Add to Home Screen** (Android/Chrome)
   or **Share → Add to Home Screen** (iOS/Safari). It'll launch full-screen like a
   native app, using the blue Adinath Visuals icon.

No further configuration is needed — the app doesn't call any external service, so
there's nothing else to set up on the GitHub side.

## Access codes

The app opens on a lock screen. Share only the code relevant to who's using the phone:

| Code | Role |
|---|---|
| `ADINATH2026` | Studio |
| `JOKUMARA2026` | Crew |

Tap the lock icon (top-right, next to the studio name) to sign out and show the
lock screen again — useful before handing the phone to someone else.

## Updating the checklist later

To change the default equipment list, edit the `catalog()` function near the top of
the `<script>` block in `index.html`, commit, and push — GitHub Pages redeploys
automatically within a minute or two.

## Notes

- All data (buckets, photos, checked state) is stored locally on the device via
  `localStorage`. It is **not** synced between devices — each phone keeps its own
  history.
- The WhatsApp button opens a chat pre-filled with the summary to **+91 82176 86375**.
  WhatsApp doesn't support deep-linking straight into a group, so for group delivery
  use the **Share** button and pick the group manually from the share sheet.
