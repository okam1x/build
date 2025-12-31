# Lift Log – Ved 💗🏋️‍♂️  
A minimalist, **offline-first** workout + bodyweight tracker built as a **PWA** (installable web app).  
No accounts. No paywalls. Just log and lift.

## ✨ Features
- **Daily workout log** (name, focus, notes)
- **Exercise tracking** per day (exercise, sets, reps, weight, RPE slider)
- **Bodyweight tracker** with a clean **14-entry trend chart**
- **Streak system** (based on “Mark today complete”)
- **Recent sessions** history (last 7 days)
- **Videos tab** with your favorite **TikTok workout clips**
  - Shoulders / Back / Arms / Abs / Legs
  - Includes **Open in TikTok** fallback button (works even if embed fails)
- **Offline support** (PWA + service worker cache)

## 🎨 Theme
Hot pink + black/grey UI (custom CSS variables) for a clean “night mode gym app” vibe.

## 🚀 Live Demo / Install
If this is hosted on GitHub Pages, you can install it like an app:
- **iOS (Safari):** Share → **Add to Home Screen**
- **Android (Chrome):** Menu → **Install app**

## 🧱 Project Structure
```txt
/
├─ index.html
├─ manifest.json
├─ sw.js
├─ icon-192.png
└─ icon-512.png
```

🛠️ Local Development

Because service workers require a proper origin, run a local server (not file://).

Option A: Python
```txt
python3 -m http.server 5173
```
Option B: Node
```txt
npx serve .
```
Then open:
	•	http://localhost:5173

📦 Deployment (GitHub Pages)
	1.	Push to GitHub
	2.	Repo → Settings → Pages
	3.	Set source to your main branch (root)
	4.	Visit your Pages URL and install the PWA

🔄 Updating the App (Important)

This project uses a cache-first service worker.
When you change index.html, bump the cache name in sw.js so the update shows up:
```txt
// sw.js
const CACHE_NAME = "ved-lift-cache-v2";
```
If you don’t bump it, your phone may keep showing the old UI.

📼 Editing the Videos Tab

Videos are stored in VIDEO_LIBRARY inside index.html.

Example:
```txt
const VIDEO_LIBRARY = {
  shoulders: [{ title: "Shoulders 1", url: "https://www.tiktok.com/t/..." }],
  back: [{ title: "Back", url: "https://www.tiktok.com/t/..." }],
};
```
TikTok Embed Notes
	•	TikTok embeds require internet (they load TikTok’s embed script)
	•	The app always shows Open in TikTok so the link works no matter what
	•	If a TikTok embed is blank, replace the short t/Z... link with the full copied URL from TikTok

🧠 Data Storage

All data is stored locally in your browser using localStorage:
	•	Key: ved_lift_log_v1
	•	Includes daily logs + bodyweight log

No cloud, no account, no tracking.

🗺️ Roadmap (ideas)
	•	Export/Import JSON backup
	•	Templates (Push/Pull/Legs)
	•	PR tracking + estimated 1RM
	•	Set-by-set logging

License
MIT 
After you paste this, click **Preview** — it should render normally (no giant gray block).
