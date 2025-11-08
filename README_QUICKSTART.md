# Letta Chatbot - Quick Start Guide

## 🚀 Get Running in 5 Minutes

### 1. Install Dependencies

```bash
cd /Users/franksimpson/CascadeProjects/letta-chatbot-railway
npm install
```

### 2. Run Locally

```bash
npm run dev
```

### 3. Open Browser

Visit: <http://localhost:3000>

---

## 🎯 What's Configured

✅ **Letta Server**: <https://lettalettalatest-production-0380.up.railway.app>  
✅ **Model**: Claude Sonnet 4.5  
✅ **Embedding**: Letta Free  
✅ **Multi-user**: Cookie-based sessions enabled  
✅ **Agent Creation**: Users can create agents from UI  

---

## 🌐 Deploy to Railway

### Option 1: Railway CLI (Fastest)

```bash
# Install CLI
npm install -g @railway/cli

# Login
railway login

# Initialize
railway init

# Set environment variables
railway variables set LETTA_BASE_URL=https://lettalettalatest-production-0380.up.railway.app
railway variables set LETTA_API_KEY=password
railway variables set USE_COOKIE_BASED_AUTHENTICATION=true
railway variables set NEXT_PUBLIC_CREATE_AGENTS_FROM_UI=true

# Deploy
railway up
```

### Option 2: GitHub + Railway Dashboard

```bash
# Push to GitHub
git init
git add .
git commit -m "Initial commit"
git remote add origin <your-repo-url>
git push -u origin main
```

Then:

1. Go to <https://railway.app/dashboard>
2. Click "New Project" → "Deploy from GitHub repo"
3. Select your repository
4. Add environment variables (see above)
5. Deploy!

---

## 📝 Customization

### Change Agent Persona

Edit `default-agent.json`:

```json
{
  "DEFAULT_MEMORY_BLOCKS": [
    {
      "label": "persona",
      "value": "Your custom persona here..."
    }
  ]
}
```

### Change Model

Edit `default-agent.json`:

```json
{
  "DEFAULT_LLM": "anthropic/claude-sonnet-4-5-20250929"
}
```

Available models:

- `anthropic/claude-sonnet-4-5-20250929`
- `anthropic/claude-haiku-4-5-20251001`
- `anthropic/claude-opus-4-1-20250805`
- `letta/letta-free`

---

## 🔧 Troubleshooting

### Can't connect to Letta server

Check `.env` file has correct values:

```env
LETTA_BASE_URL=https://lettalettalatest-production-0380.up.railway.app
LETTA_API_KEY=password
```

### Build errors

```bash
rm -rf .next node_modules
npm install
npm run build
```

### Agent creation fails

Verify the model name in `default-agent.json` matches an available model on your server.

---

## 📚 Full Documentation

See `RAILWAY_DEPLOYMENT.md` for complete deployment guide.

---

## 🎨 Tech Stack

- **Framework**: Next.js 15
- **Language**: TypeScript
- **UI**: Shadcn UI + Tailwind CSS
- **SDK**: Letta TypeScript SDK
- **Streaming**: Vercel AI SDK

---

**Ready to chat!** 🎉
