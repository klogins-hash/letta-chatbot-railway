# Letta Chatbot - Railway Deployment Guide

## 🚀 Quick Deploy to Railway

This Next.js chatbot is pre-configured for Railway deployment with your self-hosted Letta server.

---

## 📋 Prerequisites

- Railway account (https://railway.app)
- Your Letta server URL: `https://lettalettalatest-production-0380.up.railway.app`
- Your Letta API key: `password`
- Git repository (push this code to GitHub/GitLab)

---

## 🎯 Deployment Steps

### Option 1: Deploy via Railway CLI (Recommended)

1. **Install Railway CLI:**
```bash
npm install -g @railway/cli
```

2. **Login to Railway:**
```bash
railway login
```

3. **Initialize Railway project:**
```bash
cd /Users/franksimpson/CascadeProjects/letta-chatbot-railway
railway init
```

4. **Set environment variables:**
```bash
railway variables set LETTA_BASE_URL=https://lettalettalatest-production-0380.up.railway.app
railway variables set LETTA_API_KEY=password
railway variables set USE_COOKIE_BASED_AUTHENTICATION=true
railway variables set NEXT_PUBLIC_CREATE_AGENTS_FROM_UI=true
```

5. **Deploy:**
```bash
railway up
```

6. **Get your URL:**
```bash
railway domain
```

---

### Option 2: Deploy via Railway Dashboard

1. **Push to GitHub:**
```bash
cd /Users/franksimpson/CascadeProjects/letta-chatbot-railway
git init
git add .
git commit -m "Initial commit - Letta chatbot for Railway"
git remote add origin <your-github-repo-url>
git push -u origin main
```

2. **Create Railway Project:**
   - Go to https://railway.app/dashboard
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Choose your repository

3. **Configure Environment Variables:**
   In Railway dashboard, add these variables:
   ```
   LETTA_BASE_URL=https://lettalettalatest-production-0380.up.railway.app
   LETTA_API_KEY=password
   USE_COOKIE_BASED_AUTHENTICATION=true
   NEXT_PUBLIC_CREATE_AGENTS_FROM_UI=true
   ```

4. **Deploy:**
   - Railway will automatically detect Next.js
   - Build and deploy will start automatically
   - Wait for deployment to complete

5. **Get your URL:**
   - Click "Settings" → "Domains"
   - Generate a domain or add custom domain

---

## 🔧 Configuration Files

### `railway.json`
Railway-specific configuration for build and deploy settings.

### `nixpacks.toml`
Specifies Node.js 20 and build commands for Nixpacks (Railway's builder).

### `.env`
Local environment variables (already configured for your Letta server).

### `default-agent.json`
Default agent configuration:
- **Model**: `anthropic/claude-sonnet-4-5-20250929`
- **Embedding**: `letta/letta-free`
- **Persona**: Helpful AI assistant with stateful memory

---

## 🎨 Features

✅ **Modern Chat UI** - Built with Shadcn UI + Tailwind CSS  
✅ **Streaming Responses** - Real-time message streaming  
✅ **Multi-user Sessions** - Cookie-based authentication  
✅ **Agent Creation** - Users can create agents from UI  
✅ **Dark Mode** - Automatic theme switching  
✅ **Mobile Responsive** - Works on all devices  
✅ **TypeScript** - Full type safety  
✅ **Next.js 15** - Latest Next.js features  

---

## 🧪 Local Development

1. **Install dependencies:**
```bash
npm install
```

2. **Run development server:**
```bash
npm run dev
```

3. **Open browser:**
```
http://localhost:3000
```

---

## 🔐 Environment Variables

| Variable | Value | Description |
|----------|-------|-------------|
| `LETTA_BASE_URL` | `https://lettalettalatest-production-0380.up.railway.app` | Your Letta server URL |
| `LETTA_API_KEY` | `password` | Your Letta server password |
| `USE_COOKIE_BASED_AUTHENTICATION` | `true` | Enable multi-user sessions |
| `NEXT_PUBLIC_CREATE_AGENTS_FROM_UI` | `true` | Allow agent creation from UI |

---

## 📁 Project Structure

```
letta-chatbot-railway/
├── src/
│   ├── app/              # Next.js app directory
│   ├── components/       # React components
│   └── lib/             # Utility functions
├── default-agent.json   # Default agent config
├── railway.json         # Railway config
├── nixpacks.toml        # Nixpacks config
├── .env                 # Environment variables
└── package.json         # Dependencies
```

---

## 🛠️ Customization

### Change Agent Model

Edit `default-agent.json`:
```json
{
  "DEFAULT_LLM": "anthropic/claude-sonnet-4-5-20250929",
  "DEFAULT_EMBEDDING": "letta/letta-free"
}
```

Available models on your server:
- `anthropic/claude-sonnet-4-5-20250929`
- `anthropic/claude-haiku-4-5-20251001`
- `anthropic/claude-opus-4-1-20250805`
- `letta/letta-free`

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

### Customize UI Theme

Edit `tailwind.config.ts` for colors and styling.

---

## 🐛 Troubleshooting

### Build Fails
```bash
# Clear cache and rebuild
rm -rf .next node_modules
npm install
npm run build
```

### Can't Connect to Letta Server
- Verify `LETTA_BASE_URL` is correct
- Check if Letta server is running
- Verify `LETTA_API_KEY` matches server password

### Agent Creation Fails
- Check available models on your server
- Verify model name in `default-agent.json`
- Check Letta server logs

### Railway Deployment Issues
```bash
# Check Railway logs
railway logs

# Redeploy
railway up --detach
```

---

## 📊 Railway Monitoring

**View Logs:**
```bash
railway logs
```

**Check Metrics:**
- Go to Railway dashboard
- Click on your service
- View "Metrics" tab

**Restart Service:**
```bash
railway restart
```

---

## 🔄 Updates & Maintenance

### Update Dependencies
```bash
npm update
git add package.json package-lock.json
git commit -m "Update dependencies"
git push
```

### Update Letta SDK
```bash
npm install @letta-ai/letta-client@latest
npm install @letta-ai/vercel-ai-sdk-provider@latest
```

### Redeploy
Railway auto-deploys on git push, or manually:
```bash
railway up
```

---

## 🌐 Custom Domain

1. Go to Railway dashboard
2. Click your service
3. Go to "Settings" → "Domains"
4. Click "Add Domain"
5. Follow DNS configuration instructions

---

## 💰 Railway Pricing

- **Starter Plan**: $5/month (500 hours)
- **Pro Plan**: $20/month (unlimited)
- **Free Trial**: Available for new users

**Estimated Usage:**
- Small chatbot: ~$5-10/month
- Medium traffic: ~$20/month

---

## 🔗 Useful Links

**This Project:**
- Local: http://localhost:3000
- Railway: (will be generated after deployment)

**Letta Server:**
- API: https://lettalettalatest-production-0380.up.railway.app
- ADE: https://lettalettalatest-production-0380.up.railway.app (if enabled)

**Documentation:**
- Letta Docs: https://docs.letta.com
- Railway Docs: https://docs.railway.app
- Next.js Docs: https://nextjs.org/docs

**Repositories:**
- Original Template: https://github.com/letta-ai/letta-chatbot-example
- Letta TypeScript SDK: https://github.com/letta-ai/letta-node

---

## 🎯 Next Steps

1. ✅ Deploy to Railway
2. ✅ Test the chatbot
3. ✅ Customize agent persona
4. ✅ Add custom domain (optional)
5. ✅ Monitor usage and logs
6. ✅ Share with users!

---

## 📞 Support

**Letta Community:**
- Discord: https://discord.gg/letta
- GitHub Issues: https://github.com/letta-ai/letta/issues

**Railway Support:**
- Discord: https://discord.gg/railway
- Docs: https://docs.railway.app

---

**Last Updated**: November 2025  
**Letta Server**: Railway Self-hosted  
**Framework**: Next.js 15 + TypeScript  
**UI**: Shadcn UI + Tailwind CSS
