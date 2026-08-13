# MacroTracker AI

A photo-based calorie and macro tracker that installs to your phone's Home Screen.
Plain HTML/CSS/JS — no build step, no framework, no bundler. GitHub Pages serves the
folder as-is.

Live at: https://drewdessellier.github.io/grccplanner/macrotracker/

## Adding it to your Home Screen

- **iPhone/iPad (Safari):** open the link, tap **Share**, then **Add to Home Screen**.
  It must be Safari — Chrome on iOS cannot install web apps.
- **Android (Chrome):** open the link and tap **Install** in the banner, or use the
  browser menu's **Install app**.

Once installed it launches full screen with no browser chrome, and the log stays
readable offline.

## API key

Meal analysis calls Google's Gemini API directly from the browser, so the app needs
your own key. Get a free one at https://aistudio.google.com/apikey, then tap the key
icon in the header and paste it.

The key is stored in `localStorage` on that device only — it is never committed to
this repo and never sent anywhere except Google's API. Because this repository is
public, do not hardcode a key into any file here. Each device (and each browser)
needs the key entered once.

## Where your data lives

Everything is local to the device: meals and your calorie target in `localStorage`,
meal photos in IndexedDB. Nothing syncs between devices, and clearing site data wipes
the log.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app — markup, styles, and logic |
| `manifest.webmanifest` | PWA metadata: name, icons, standalone display |
| `sw.js` | Service worker caching the app shell for offline use |
| `icon-*.png`, `apple-touch-icon.png` | Home Screen icons |

After changing any shell file, bump `CACHE` in `sw.js` so installed copies pick up the
new version instead of serving the stale cache.
