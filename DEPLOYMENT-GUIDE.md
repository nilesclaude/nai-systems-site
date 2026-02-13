# NAI Systems Website - Deployment Guide

## Quick Overview

**Domain:** naisystems.online  
**Hosting:** GoDaddy  
**Deployment:** GitHub + Vercel  
**Contact Email:** contact@naisystems.online

---

## Step 1: GitHub Repository Setup

### A. Create GitHub Account (if needed)
1. Go to [github.com](https://github.com)
2. Sign up / Log in
3. Verify your email

### B. Create New Repository
1. Click the **+** icon (top right) → "New repository"
2. Repository name: `naisystems-website`
3. Description: "NAI Systems corporate website - naisystems.online"
4. Visibility: **Public** (required for free Vercel hosting)
5. **Do NOT** check "Initialize with README" (we have files already)
6. Click "Create repository"

### C. Copy Your Repository URL
You'll see something like:
```
https://github.com/YOUR_USERNAME/naisystems-website.git
```
**Copy this URL** - we'll need it in Step 2.

---

## Step 2: Push Website Files to GitHub

### Option A: Using Git Command Line

1. **Open PowerShell/Terminal** in the `naisystems-website` folder

2. **Initialize Git:**
```bash
git init
```

3. **Add all files:**
```bash
git add .
```

4. **Commit:**
```bash
git commit -m "Initial website deployment"
```

5. **Add your GitHub repo as remote** (replace with YOUR URL):
```bash
git remote add origin https://github.com/YOUR_USERNAME/naisystems-website.git
```

6. **Push to GitHub:**
```bash
git push -u origin main
```

If it asks for branch name, try:
```bash
git branch -M main
git push -u origin main
```

### Option B: Using GitHub Desktop (Easier)

1. Download [GitHub Desktop](https://desktop.github.com/)
2. Install and sign in with your GitHub account
3. File → "Add Local Repository"
4. Choose the `naisystems-website` folder
5. Click "Publish repository" button
6. Confirm it's public and publish

---

## Step 3: Deploy to Vercel

### A. Sign Up for Vercel
1. Go to [vercel.com](https://vercel.com)
2. Click "Sign Up"
3. **Use "Continue with GitHub"** (easiest!)
4. Authorize Vercel to access your GitHub account

### B. Import Project
1. From Vercel dashboard, click "Add New..." → "Project"
2. You'll see your GitHub repositories listed
3. Find `naisystems-website` and click **"Import"**

### C. Configure Project
1. **Framework Preset:** Select "Other" (it's just static HTML)
2. **Root Directory:** Leave as `.` (default)
3. **Build Command:** Leave blank
4. **Output Directory:** Leave blank
5. Click **"Deploy"**

Vercel will:
- Pull your code from GitHub
- Generate a temporary URL like `naisystems-website-abc123.vercel.app`
- Deploy in ~30 seconds

### D. Verify Deployment
1. Click the generated URL
2. Check that your website loads correctly
3. Test all pages (Home, Capabilities, Portfolio, Pricing, About, Contact)

---

## Step 4: Connect Your GoDaddy Domain

### A. Get Vercel DNS Settings
1. In Vercel project dashboard, go to **Settings** → **Domains**
2. Click "Add Domain"
3. Type: `naisystems.online`
4. Vercel will give you DNS configuration options
5. Choose **"A Record"** method (recommended for GoDaddy)

Vercel will show you something like:
```
Type: A
Name: @
Value: 76.76.21.21
```

### B. Configure GoDaddy DNS
1. Log in to [godaddy.com](https://godaddy.com)
2. Go to "My Products" → "Domains"
3. Click on `naisystems.online` → "Manage DNS"

4. **Add A Record for root domain:**
   - Type: `A`
   - Name: `@`
   - Value: `76.76.21.21` (Vercel's IP - copy from Vercel settings)
   - TTL: 600 seconds (default)
   - Click "Save"

5. **Add A Record for www subdomain:**
   - Type: `A`
   - Name: `www`
   - Value: `76.76.21.21` (same IP)
   - TTL: 600 seconds
   - Click "Save"

6. **Optional: Add CNAME for Vercel (alternative method):**
   - Type: `CNAME`
   - Name: `www`
   - Value: `cname.vercel-dns.com`
   - TTL: 600 seconds

### C. Wait for DNS Propagation
- DNS changes take **5-60 minutes** to propagate
- Check status at: [dnschecker.org](https://dnschecker.org)
- Enter `naisystems.online` to see if it's live globally

### D. Verify in Vercel
1. Back in Vercel → Settings → Domains
2. Your domain should show **"Valid Configuration"** ✅
3. SSL certificate will auto-provision (https enabled automatically)

---

## Step 5: Set Up Email (contact@naisystems.online)

### Option A: GoDaddy Email Forwarding (Free)
1. In GoDaddy → Domains → Manage
2. Email → "Manage" → "Email Forwarding"
3. Create forwarding rule:
   - Forward from: `contact@naisystems.online`
   - Forward to: Your personal email
4. Save and verify

### Option B: Full Email Hosting (Paid)
1. GoDaddy offers email hosting (~$2-5/month)
2. Or use Google Workspace / Microsoft 365
3. Configure MX records in GoDaddy DNS

---

## Step 6: Test Everything

### Website Checklist
- [ ] `naisystems.online` loads correctly
- [ ] `www.naisystems.online` works (redirects to non-www or vice versa)
- [ ] HTTPS works (green padlock in browser)
- [ ] All navigation links work
- [ ] Contact form displays (functionality placeholder)
- [ ] Mobile responsive design works
- [ ] Fast page load times

### Email Test
- [ ] Send test email to `contact@naisystems.online`
- [ ] Verify it reaches your inbox
- [ ] Reply from business email works

---

## Step 7: Future Updates

### Making Changes to the Website

**Method 1: Direct Edit on GitHub**
1. Go to your GitHub repo
2. Click on the file you want to edit
3. Click the pencil icon (Edit)
4. Make changes
5. Scroll down → "Commit changes"
6. Vercel auto-deploys in ~30 seconds!

**Method 2: Local Edit + Push**
1. Edit files locally
2. Git add, commit, push:
```bash
git add .
git commit -m "Updated pricing page"
git push
```
3. Vercel auto-deploys

**Method 3: Ask Niles**
- Message me with updates needed
- I'll edit files and commit to GitHub
- Automatic deployment via Vercel

---

## Troubleshooting

### Domain not connecting?
- Check GoDaddy DNS records are correct
- Wait 30-60 minutes for propagation
- Use [whatsmydns.net](https://whatsmydns.net) to check status
- Verify Vercel shows domain as "Valid"

### Website changes not showing?
- Clear browser cache (Ctrl+F5)
- Check GitHub repo has latest commit
- Check Vercel deployment log (Deployments tab)
- Vercel auto-deploys on every push to main branch

### Email not working?
- Verify email forwarding is set up in GoDaddy
- Check spam folder
- MX records may take longer to propagate

### SSL certificate not working?
- Vercel provisions SSL automatically
- Can take up to 24 hours (usually 10 minutes)
- Check Vercel → Settings → Domains → SSL status

---

## Architecture Summary

```
Local Files (naisystems-website/)
    ↓ (git push)
GitHub Repository (source of truth)
    ↓ (auto-deploy trigger)
Vercel (hosting + CI/CD)
    ↓ (DNS configured)
GoDaddy Domain (naisystems.online)
    ↓
Users see: https://naisystems.online
```

**Benefits of this setup:**
- ✅ Free hosting (Vercel)
- ✅ Free SSL (Vercel auto-provisions)
- ✅ Auto-deployment (push to GitHub = instant deploy)
- ✅ Version control (GitHub keeps history)
- ✅ Easy rollback (deploy any previous commit)
- ✅ Fast CDN (Vercel's global edge network)

---

## Support

**Need help?** Message Niles:
- Discord: #niles-planning channel
- Email: nilesclaude@gmail.com (once OAuth setup)

**External Resources:**
- Vercel Docs: https://vercel.com/docs
- GitHub Docs: https://docs.github.com
- GoDaddy DNS Help: https://www.godaddy.com/help/dns

---

**Ready to deploy!** 🚀

Follow the steps above and your website will be live at https://naisystems.online

Let me know once you've completed Steps 1-2 (GitHub setup) and I can help verify everything looks good before Vercel deployment.
