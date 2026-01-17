# Netlify Deployment Guide

## Step 1: Push to GitHub
1. Go to github.com
2. Sign up/login
3. Create new repository: "practical-ai"
4. Follow commands in GITHUB_SETUP_COMMANDS.txt

## Step 2: Connect Netlify to GitHub
1. Go to netlify.com
2. Click "Add new site" → "Import an existing project"
3. Choose "GitHub"
4. Authorize Netlify to access GitHub
5. Select the "practical-ai" repository

## Step 3: Configure Build Settings
Netlify should auto-detect settings from netlify.toml, but verify:
- Base directory: `website`
- Build command: `npm run build`
- Publish directory: `website/dist`

## Step 4: Deploy
1. Click "Deploy site"
2. Wait 2-3 minutes for build
3. Get your live URL!

## Step 5: Automatic Deployments
Now whenever you:
1. Make changes to files
2. Commit to git
3. Push to GitHub
→ Netlify automatically rebuilds and deploys!

## Future Updates
```bash
# Make changes to files
git add .
git commit -m "Update website content"
git push

# Netlify auto-deploys within 2-3 minutes
```
