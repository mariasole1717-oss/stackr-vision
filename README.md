# STACKR Vision — Deploy to Vercel

Anyone opens the link. No API key. No setup. Just works.

---

## What's in this folder

```
stackr-deploy/
├── api/
│   └── chat.js        ← Server function (holds your secret API key)
├── public/
│   └── index.html     ← The full app (no API key in the code)
└── vercel.json        ← Routing config
```

---

## Deploy in 5 minutes (free)

### Step 1 — Create a GitHub repo

1. Go to **github.com** → click **New repository**
2. Name it `stackr-vision`, set it to **Public**, click **Create**
3. Upload all three files maintaining the folder structure:
   - `api/chat.js`
   - `public/index.html`
   - `vercel.json`

   Easiest way: click **uploading an existing file** → drag the whole `stackr-deploy` folder

### Step 2 — Connect to Vercel

1. Go to **vercel.com** → sign up free with your GitHub account
2. Click **Add New Project**
3. Select your `stackr-vision` repo → click **Import**
4. Leave all settings as default → click **Deploy**

### Step 3 — Add your API key (the important bit)

1. After deploy, go to your project dashboard on Vercel
2. Click **Settings** → **Environment Variables**
3. Add a new variable:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-...` (your full key from console.anthropic.com)
   - **Environment:** Production, Preview, Development (tick all)
4. Click **Save**
5. Go to **Deployments** → click the three dots on your latest deploy → **Redeploy**

### Step 4 — Share your link

Vercel gives you a URL like:
```
https://stackr-vision.vercel.app
```

Share this with anyone. They open it, click "Start Screen Scan", and STACKR works immediately — no API key, no setup, no install.

---

## How it works (for your class presentation)

```
User's browser                Your Vercel server          Anthropic
──────────────                ─────────────────          ──────────
Opens app        ──────────►  Serves index.html
Shares screen
Takes screenshot ──────────►  /api/chat                 
                              Adds secret API key  ────► Claude Vision
                              ◄────────────────────      Returns tip
Shows tip        ◄──────────  Returns response
```

Your API key never touches the user's browser. It lives only on Vercel's servers.

---

## Cost estimate

Claude Sonnet pricing: ~$3 per million input tokens.
One screen scan ≈ 2,000 tokens (image + prompt).
**1,000 scans ≈ $6.** For a class demo with ~20 people, you're looking at cents.

---

## Updating the app

Just push changes to GitHub — Vercel auto-deploys in ~30 seconds.
