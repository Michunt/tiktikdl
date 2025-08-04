# API Hosting Options for TikViddl

Your frontend is live on Netlify, but it needs a backend API to work. Here are your options:

## Option 1: Render.com (Easiest & Free)
**Pros:**
- ✅ Free tier available
- ✅ No credit card required
- ✅ Easy GitHub integration
- ✅ Automatic deploys

**Cons:**
- ❌ Sleeps after 15 minutes of inactivity
- ❌ First request after sleep takes ~30 seconds

**How to deploy:** See QUICK_API_DEPLOYMENT.md

---

## Option 2: Railway.app (Good Free Trial)
**Pros:**
- ✅ $5 free credit monthly
- ✅ Super easy deployment
- ✅ No sleep on free tier
- ✅ Better performance

**Cons:**
- ❌ Requires credit card after trial
- ❌ Limited to $5/month free

**How to deploy:**
1. Go to https://railway.app
2. Click "Start a New Project"
3. Select "Deploy from GitHub repo"
4. Choose your repository
5. Add environment variables from `.env.tiktok`
6. Deploy automatically starts

---

## Option 3: Vercel (Frontend + API)
**Pros:**
- ✅ Free tier
- ✅ Can host both frontend and API
- ✅ Serverless functions

**Cons:**
- ❌ Requires code changes for serverless
- ❌ 10-second timeout limit

---

## Option 4: Heroku (If you have existing account)
**Pros:**
- ✅ Reliable
- ✅ Good free tier (if grandfathered)

**Cons:**
- ❌ No more free tier for new accounts
- ❌ Requires credit card

---

## Option 5: Google Cloud Run (Professional)
**Pros:**
- ✅ Scales to zero
- ✅ Pay only for usage
- ✅ Very reliable

**Cons:**
- ❌ More complex setup
- ❌ Requires billing account

---

## Option 6: Your Own VPS (Best for Production)
**Pros:**
- ✅ Full control
- ✅ Best performance
- ✅ No limitations

**Cons:**
- ❌ Costs money ($5-10/month)
- ❌ Requires server management

**Providers:**
- DigitalOcean ($6/month)
- Linode ($5/month)
- Vultr ($6/month)

---

## For Testing Only: Run Locally with Ngrok

If you just want to test quickly:

1. **Run API locally:**
   ```bash
   cd api
   npm install
   node src/cobalt-tiktok.js
   ```

2. **Install ngrok:**
   - Download from https://ngrok.com/download
   - Sign up for free account
   - Get your auth token

3. **Expose your local API:**
   ```bash
   ngrok http 9000
   ```

4. **Update Netlify:**
   - Copy the ngrok URL (like `https://abc123.ngrok.io`)
   - Go to Netlify → Site settings → Environment variables
   - Add: `VITE_API_URL` = `https://abc123.ngrok.io`
   - Redeploy your site

---

## Recommendation

**For Testing:** Use Render.com or local + ngrok
**For Production:** Use Railway.app or your own VPS

The most important thing is to get your API online somewhere so your Netlify site can connect to it!
