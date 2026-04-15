# 🎬 Cutscene Manager — Owlbear Rodeo Extension

A GM tool for creating and triggering **cinematic cutscenes** during your TTRPG sessions.
Organize scenes with images, captions, ambient audio, and visual effects. Trigger them live for all players in one click.

---

## ✨ Features

| Feature | Details |
|---|---|
| **Scene Library** | Create unlimited named scenes, organized in the GM panel |
| **Images** | Display any image via URL (PNG, JPG, WebP) |
| **Captions** | Italic serif text displayed below the image |
| **Audio** | Any MP3/OGG URL — auto-loops with fade-in/out |
| **Entrance Effects** | Fade In, Flash (with particles), Slide Up, Zoom In, Reveal |
| **Mood Backgrounds** | Black, Dark Blue, Sepia, Blood Red, Dark Forest |
| **Cinematic Letterbox** | Optional widescreen bars for a movie feel |
| **Auto-close Timer** | Scene closes after N seconds (0 = manual) |
| **GM Preview** | Preview a scene locally before triggering for players |
| **LIVE indicator** | Badge shows when a scene is active for players |

---

## 📁 Files

```
cutscene-manager/
├── manifest.json      ← Extension manifest (load this URL into OBR)
├── gm.html            ← GM control panel (action popover)
├── player.html        ← Full-screen player overlay (cinematic view)
├── background.html    ← Silent background listener (broadcasts handler)
├── icon.svg           ← Extension icon
└── README.md
```

---

## 🚀 Setup: Deploy in 3 Steps

### Step 1 — Host the files

You need to host these files on a public HTTPS server.

**Option A – Netlify (free, easiest)**
1. Go to [netlify.com](https://netlify.com) and sign up for free
2. Drag this entire `cutscene-manager` folder onto the Netlify deploy zone
3. You'll get a URL like `https://your-name.netlify.app`

**Option B – GitHub Pages (free)**
1. Create a new GitHub repository
2. Push all these files to the repo
3. Go to Settings → Pages → Deploy from branch → main
4. Your URL will be `https://yourusername.github.io/repo-name/`

**Option C – Any static host**
Vercel, Cloudflare Pages, Firebase Hosting, or any web server that supports HTTPS.

> ⚠️ **HTTPS is required.** Owlbear Rodeo only loads extensions over HTTPS.

---

### Step 2 — Update `manifest.json`

Open `manifest.json` and update the author field:
```json
{
  "author": "Your Name Here"
}
```

No other changes needed — all URLs are relative.

---

### Step 3 — Load into Owlbear Rodeo

1. Open your Owlbear Rodeo room
2. Click the **plug icon (Extensions)** in the top-right
3. Click **Add Extension**
4. Paste your manifest URL, e.g.:
   `https://your-name.netlify.app/manifest.json`
5. Click **Add** — the 🎬 icon will appear in your toolbar!

---

## 🎭 How to Use

### GM Side
1. Click the **🎬 Cutscene Manager** icon in OBR
2. Click **+** to create a new scene
3. Fill in the fields:
   - **Scene Name** — for your own reference
   - **Image URL** — paste a direct link to any image
   - **Caption** — atmospheric text shown below the image
   - **Audio URL** — link to an MP3 for ambience music/sound
   - **Entrance Effect** — choose how it appears
   - **Auto-close** — 0 means players see it until you stop it
4. Click **👁 Preview** to see it yourself first
5. Click **▶ Trigger** to show it to all players
6. Click **⏹** (stop button) to dismiss the scene for everyone

### Players
Players just see the cutscene appear automatically — no action needed!

---

## 🎵 Free Audio Resources

- [Freesound.org](https://freesound.org) — Creative Commons sounds
- [Tabletop Audio](https://tabletopaudio.com) — Ambient RPG music
- [OpenGameArt](https://opengameart.org/content/music) — Free game music

> Get a **direct link** ending in `.mp3` or `.ogg` — not a webpage URL.
> Use the "Copy audio link" option or check the browser network tab.

---

## 🖼️ Free Image Resources

- [Unsplash](https://unsplash.com) — High quality photos
- [ArtStation](https://artstation.com) — Fantasy art
- [Midjourney](https://midjourney.com) — AI-generated fantasy art
- [Reddit r/ImaginaryLandscapes](https://reddit.com/r/ImaginaryLandscapes)

> Use **direct image URLs** ending in `.jpg`, `.png`, or `.webp`.

---

## 🛠️ Troubleshooting

| Problem | Fix |
|---|---|
| Images not showing | Make sure the URL is a direct image link (ends in .jpg/.png/.webp), not a webpage |
| Audio not playing | Browsers block autoplay — user needs to interact with OBR first. The audio will play on reload after interaction. |
| Players not seeing cutscene | Check they have the extension installed in their room. The background.html must be loaded. |
| Extension not loading | Verify your server uses HTTPS, not HTTP |
| CORS errors | Some image hosts block cross-origin. Use imgur, Discord CDN, or your own hosting |

---

## 📦 Tech Stack

- **OBR SDK** `@owlbear-rodeo/sdk` (via esm.sh CDN, no build required)
- **Vanilla HTML/CSS/JS** — no frameworks, no build step
- **OBR APIs used:**
  - `OBR.room.setMetadata / getMetadata` — scene storage
  - `OBR.broadcast.sendMessage / onMessage` — GM → player communication
  - `OBR.modal.open / close` — player overlay
  - `OBR.player.getRole` — GM vs Player check

---

## 📄 License

MIT — free to use, modify, and share.
