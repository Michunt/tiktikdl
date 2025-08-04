# Quick API Deployment Guide

## The Issue
Your frontend is deployed on Netlify, but it needs a backend API to actually download TikTok videos. The API needs to be deployed separately.

## Quick Solution Options

### Choose One of These Options:

### Option 1: Deploy API on Render.com (Recommended - Free)
1. Go to https://render.com and sign up
2. Click "New +" → "Web Service"
3. Connect your GitHub account
4. Select your `Michunt/tiktikdl` repository
5. Use these settings:
   - **Name**: tiktikdl-api
   - **Root Directory**: api
   - **Build Command**: `npm install`
   - **Start Command**: `node src/cobalt-tiktok.js`
   - **Instance Type**: Free
6. Add these Environment Variables (click "Advanced"):
   - `API_URL`: https://tiktikdl-api.onrender.com/
   - `API_PORT`: 10000
   - `CORS_WILDCARD`: 1
   - Copy other variables from `.env.tiktok`
7. Click "Create Web Service"
8. Wait for deployment (takes 5-10 minutes)
9. Copy your API URL (like `https://tiktikdl-api.onrender.com`)

### Option 2: Update Netlify Environment Variable
Once your API is deployed:
1. Go to Netlify dashboard
2. Site settings → Environment variables
3. Add: `VITE_API_URL` = `https://your-api-url.onrender.com`
4. Redeploy your site

### Option 3: Quick Local Testing (Not for Production)
If you want to test locally first:
1. Run the API locally: 
   ```
   cd api
   npm install
   node src/cobalt-tiktok.js
   ```
2. Use ngrok to expose it: `ngrok http 9000`
3. Update Netlify env var with ngrok URL

## Important Notes
- The free Render.com tier spins down after 15 minutes of inactivity
- First request after spin-down takes ~30 seconds
- For production, consider paid hosting for better performance
