# PathfinderAI — Deployment Guide

## What's in this folder
- `index.html` — The complete PathfinderAI web app (self-contained)
- `netlify/functions/chat.js` — Serverless function that securely proxies API calls to Anthropic
- `netlify.toml` — Netlify configuration

## Deploy to a shareable URL (5 minutes)

### Step 1: Get an Anthropic API key
1. Go to https://console.anthropic.com
2. Create an account or sign in
3. Go to API Keys → Create Key
4. Copy the key (starts with `sk-ant-...`)

### Step 2: Deploy to Netlify (free)
1. Go to https://app.netlify.com and sign up (free, use GitHub/email)
2. Click "Add new site" → "Deploy manually"
3. Drag and drop this entire `pathfinder-site` folder onto the upload area
4. Wait ~30 seconds for deployment

### Step 3: Add your API key
1. In Netlify, go to your new site → Site settings → Environment variables
2. Click "Add a variable"
3. Key: `ANTHROPIC_API_KEY`
4. Value: paste your API key from Step 1
5. Click Save
6. Go to Deploys → Trigger deploy → Deploy site (redeploy to pick up the env var)

### Step 4: Share
Your site is now live at something like `https://random-name-123.netlify.app`
You can set a custom name: Site settings → Domain management → Change site name
e.g. `https://pathfinder-ai-demo.netlify.app`

Share this URL with anyone — they can use it immediately, no login required.

## Costs
- Netlify hosting: Free (125k function invocations/month)
- Anthropic API: ~$0.003 per conversation exchange (Claude Sonnet)
- A typical demo session (10 messages) costs roughly $0.03

## Local testing
To test locally before deploying, you can install the Netlify CLI:
```
npm install -g netlify-cli
cd pathfinder-site
netlify dev
```
This will run the site locally with the serverless function.

## Notes
- This is a prototype with sample data modelled on public HESA/Discover Uni sources
- Programme data, fees, and outcome figures are illustrative — not live
- For production, you'd want: real-time data feeds, user authentication, analytics, and proper hosting
