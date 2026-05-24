# 🏏 CricScore — Live Cricket Scoreboard

Real-time cricket score calculator for GitHub Pages. One scorer updates; 50+ viewers see it live.

---

## ✅ What's New in This Version
- 🌙 Light/Dark theme toggle
- 🔔 Innings complete notification with a "Start 2nd Innings" button
- 🔒 Visible "Unlock Scorer" button for viewers — no hidden tabs
- 🎯 Better local testing instructions built into the app
- 📋 Share URL button built in

---

## 🔥 Firebase Setup (Step by Step with Screenshots Guide)

### Step 1 — You already have Realtime Database ✅
Your database URL is: `https://cricscorebyhg-default-rtdb.firebaseio.com`
This is your `databaseURL` value.

### Step 2 — Get the rest of the config values
1. In Firebase Console, click the **gear icon ⚙️** (top-left, next to "Project Overview")
2. Click **"Project settings"**
3. Scroll down to the **"Your apps"** section
4. If no app exists: click the **`</>`** (Web) icon → give it any name → click **Register app**
5. You'll see a code block like this — copy ALL values:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "cricscorebyhg.firebaseapp.com",
  databaseURL: "https://cricscorebyhg-default-rtdb.firebaseio.com",
  projectId: "cricscorebyhg",
  storageBucket: "cricscorebyhg.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

### Step 3 — Paste into index.html
Open `index.html`, find this block (search for `REPLACE_WITH_YOUR`):

```js
const firebaseConfig = {
  apiKey:            "REPLACE_WITH_YOUR_apiKey",
  authDomain:        "REPLACE_WITH_YOUR_authDomain",
  databaseURL:       "REPLACE_WITH_YOUR_databaseURL",
  ...
};
```

Replace each value. Make sure `databaseURL` is set to your Realtime DB URL.

### Step 4 — Firebase Rules (allow read/write)
In Firebase Console → Realtime Database → **Rules** tab, set:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
Click **Publish**. This allows all viewers to read scores.

### Step 5 — Push to GitHub & enable Pages
1. Create a GitHub repo (public)
2. Add `index.html` to the repo
3. Go to repo **Settings → Pages → Source: Deploy from branch → main → / (root)**
4. Your URL: `https://yourusername.github.io/your-repo/`

---

## 📱 How to Use

### You (Scorer)
1. Open the GitHub Pages URL
2. Fill in team names, overs, set a scorer password → **Start Match**
3. You're automatically in scorer mode — tap the scoring buttons
4. Tap **Share URL 📋** to copy the link and send to viewers via WhatsApp/SMS

### Viewers
- Open the same URL — they see the live scoreboard
- It auto-updates every time you score a ball
- They can tap "Unlock Scorer" and enter the password if they want to help score

---

## 💻 Local Testing (without hosting)

URL sharing across devices won't work on `file://` — use one of these:

**Option A — VS Code Live Server** (easiest)
- Install "Live Server" extension in VS Code
- Right-click `index.html` → Open with Live Server
- Opens at `http://localhost:5500`

**Option B — Terminal**
```bash
npx serve .
# opens http://localhost:3000
```

**Option C — Python**
```bash
python3 -m http.server 8080
# opens http://localhost:8080
```

**Testing two views on same device:**
Open two browser tabs on `http://localhost:PORT` — one as scorer, one as viewer. Firebase syncs between them!

---

## 🧩 Features
| Feature | Detail |
|---|---|
| Runs | 0–6 per ball |
| Extras | Wide +1, No Ball +1 (no ball count added) |
| Wickets | Up to 10, auto detects all-out |
| Overs | Auto-calculated, custom over count supported |
| Run Rate | Live RR and Required RR (2nd innings) |
| Innings notification | Banner + button when 1st innings ends |
| Undo | Last ball can be undone |
| Theme | Light and dark mode, saved in browser |
| Live sync | Firebase free tier, 100 concurrent users |
| Password | Scorer controls protected by password |

