# YouTube Channel Sentiment Analyzer

AI-powered dashboard to analyze comment sentiment across your entire YouTube channel.
Built with YouTube Data API v3 + Claude (Anthropic).

---

## Project Structure

```
yt-sentiment/
├── public/
│   └── index.html          ← The dashboard (your frontend)
├── netlify/
│   └── functions/
│       └── claude.js       ← Serverless proxy for Netlify
├── api/
│   └── claude.js           ← Serverless proxy for Vercel
├── netlify.toml            ← Netlify config
└── vercel.json             ← Vercel config
```

---

## Deploy to Netlify (recommended — free tier is plenty)

### Step 1 — Push to GitHub
```bash
git init
git add .
git commit -m "yt sentiment dashboard"
git remote add origin https://github.com/YOUR_USERNAME/yt-sentiment.git
git push -u origin main
```

### Step 2 — Connect to Netlify
1. Go to https://app.netlify.com → **Add new site** → **Import from Git**
2. Pick your GitHub repo
3. Build settings are auto-detected from `netlify.toml`:
   - **Publish directory:** `public`
   - **Functions directory:** `netlify/functions`
4. Click **Deploy site**

### Step 3 — Add your Anthropic API key
1. In Netlify: **Site Settings** → **Environment variables** → **Add variable**
2. Key: `ANTHROPIC_API_KEY`
3. Value: your Anthropic API key (`sk-ant-...`)
4. **Redeploy** the site (Deploys → Trigger deploy)

### Step 4 — Use the dashboard
Open your Netlify URL → enter your YouTube API key + channel handle → click Analyze!

---

## Deploy to Vercel (alternative)

### Step 1 — Push to GitHub (same as above)

### Step 2 — Import to Vercel
1. Go to https://vercel.com/new → Import your repo
2. Framework: **Other** (no framework needed)
3. Output Directory: `public`
4. Click **Deploy**

### Step 3 — Add environment variable
1. In Vercel: **Project Settings** → **Environment Variables**
2. Key: `ANTHROPIC_API_KEY` → Value: `sk-ant-...`
3. **Redeploy** from the Deployments tab

---

## Keys you need

| Key | Where to get it | Cost |
|-----|----------------|------|
| YouTube Data API v3 | console.cloud.google.com → Enable API → Credentials | Free (10k units/day) |
| Anthropic API key | console.anthropic.com → API Keys | Pay per use (~$0.01–0.05 per analysis) |

---

## Notes
- Your YouTube API key is entered in the browser UI — it's only sent to Google's API directly
- Your Anthropic key lives only in Netlify/Vercel environment variables — never exposed to the browser
- YouTube free quota: 10,000 units/day ≈ 10–20 full channel analyses per day
