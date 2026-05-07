# Mirayah — Deployment Guide

## Deploy to Vercel (free, 5 minutes)

### Step 1 — Get your free Gemini API key
1. Go to **aistudio.google.com**
2. Sign in with Google
3. Click **"Get API Key"** → **"Create API key"**
4. Copy the key (starts with `AIza...`)

### Step 2 — Upload to GitHub
1. Go to **github.com** and create a free account if you don't have one
2. Click **"New repository"** → name it `mirayah` → click **"Create repository"**
3. Upload these files by dragging them into the GitHub interface:
   - `vercel.json`
   - `api/reflect.js`
   - `public/index.html`

### Step 3 — Deploy on Vercel
1. Go to **vercel.com** → sign up free with your GitHub account
2. Click **"Add New Project"** → import your `mirayah` repository
3. Click **"Deploy"** — Vercel builds it automatically

### Step 4 — Add your Gemini API key
1. In your Vercel project → go to **Settings** → **Environment Variables**
2. Add a new variable:
   - **Name:** `GEMINI_API_KEY`
   - **Value:** paste your `AIza...` key
3. Click **Save** → go to **Deployments** → **Redeploy**

### Done!
Vercel gives you a live URL like `mirayah.vercel.app` — share it with anyone.
Users open it and it just works. No login, no setup, no API key needed from them.

---

## Project structure
```
mirayah/
├── vercel.json          # Vercel routing config
├── api/
│   └── reflect.js       # Serverless function — holds your Gemini key
└── public/
    └── index.html       # The full Mirayah app
```

## How it works
- User submits a reflection in the browser
- Browser calls `/api/reflect` on YOUR Vercel server
- Your server adds the Gemini API key and calls Google
- Response comes back to the user
- Your key is never exposed to anyone

## Free tier limits
- **Vercel:** 100GB bandwidth/month, unlimited deployments — free forever
- **Gemini 1.5 Flash:** 1,500 requests/day, 1M tokens/minute — free forever

Built by Mahmoud Ismail — v0.1.0-alpha
