# TikViddl Deployment Guide

## Netlify Deployment Instructions

### Prerequisites
- A Netlify account (sign up at https://www.netlify.com)
- This repository pushed to GitHub

### Deployment Steps

1. **Log in to Netlify**
   - Go to https://app.netlify.com
   - Sign in with your GitHub account

2. **Import the Project**
   - Click "Add new site" → "Import an existing project"
   - Choose "Deploy with GitHub"
   - Authorize Netlify to access your GitHub account
   - Select the `Michunt/tiktikdl` repository

3. **Configure Build Settings**
   The `netlify.toml` file already contains the configuration, but verify:
   - **Build command**: `cd web && npm install && npm run build`
   - **Publish directory**: `web/dist`
   - **Node version**: 18

4. **Set Environment Variables**
   In Netlify dashboard, go to Site settings → Environment variables and add:
   - `VITE_API_URL`: Your API endpoint URL (e.g., `https://your-api-server.com`)
   
   Note: You'll need to deploy the API separately (see API Deployment section below)

5. **Deploy**
   - Click "Deploy site"
   - Wait for the build to complete (usually 1-3 minutes)
   - Your site will be live at a Netlify URL like `https://amazing-site-123.netlify.app`

6. **Custom Domain (Optional)**
   - Go to Domain settings
   - Add your custom domain
   - Follow Netlify's DNS configuration instructions

## API Deployment Options

The web frontend needs an API backend to function. Here are deployment options:

### Option 1: Deploy API on Render.com
1. Create account at https://render.com
2. Create new Web Service
3. Connect your GitHub repository
4. Use these settings:
   - **Build Command**: `cd api && npm install`
   - **Start Command**: `cd api && node src/cobalt-tiktok.js`
   - **Environment Variables**: Set according to `.env.tiktok`

### Option 2: Deploy API on Railway.app
1. Create account at https://railway.app
2. Create new project from GitHub
3. Add environment variables from `.env.tiktok`
4. Deploy will start automatically

### Option 3: Deploy API on Heroku
1. Install Heroku CLI
2. Create `Procfile` in api directory:
   ```
   web: node src/cobalt-tiktok.js
   ```
3. Deploy using Heroku Git

### Option 4: Deploy API on VPS
1. Clone repository on your VPS
2. Install Node.js 18+
3. Install PM2: `npm install -g pm2`
4. Start API: `pm2 start api/src/cobalt-tiktok.js`
5. Setup nginx reverse proxy

## Important Notes

1. **CORS Configuration**: Make sure your API's CORS settings allow requests from your Netlify domain
2. **HTTPS Required**: Both frontend and API should use HTTPS in production
3. **Rate Limiting**: Configure appropriate rate limits in production
4. **API Keys**: If using API authentication, secure your keys properly

## Testing Your Deployment

1. Visit your Netlify URL
2. Try downloading a TikTok video
3. Check browser console for any errors
4. Verify API connectivity

## Troubleshooting

- **API Connection Failed**: Check VITE_API_URL environment variable
- **CORS Errors**: Update API CORS settings to include Netlify domain
- **Build Failures**: Check Node version and build logs
- **404 Errors**: Ensure `netlify.toml` redirects are configured

## Support

For issues specific to:
- Netlify deployment: Check Netlify docs or support
- API issues: Check the API logs
- Application bugs: Create issue on GitHub
