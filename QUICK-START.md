# NAI Systems Website - Quick Start Checklist

**Goal:** Get naisystems.online live in 30 minutes

---

## ✅ Pre-Flight Check

**Before you start, make sure you have:**
- [ ] GitHub account created
- [ ] Git installed on your PC (or GitHub Desktop)
- [ ] GoDaddy account access for naisystems.online
- [ ] 30 minutes of uninterrupted time

---

## 🚀 Deployment Steps

### 1. GitHub Setup (5 minutes)
- [ ] Go to github.com/new
- [ ] Name: `naisystems-website`
- [ ] Public repository
- [ ] Don't initialize with README
- [ ] Create repository
- [ ] **Copy the repo URL** (you'll need it next)

### 2. Push Code to GitHub (5 minutes)

**Option A - Command Line:**
```bash
cd C:\Users\niles\.openclaw\workspace\naisystems-website
git init
git add .
git commit -m "Initial website deployment"
git remote add origin YOUR_REPO_URL_HERE
git branch -M main
git push -u origin main
```

**Option B - GitHub Desktop:**
- Open GitHub Desktop
- Add Local Repository → Choose naisystems-website folder
- Publish repository

### 3. Deploy to Vercel (5 minutes)
- [ ] Go to vercel.com
- [ ] Sign up with GitHub
- [ ] Click "Add New..." → "Project"
- [ ] Import `naisystems-website`
- [ ] Framework: "Other"
- [ ] Click "Deploy"
- [ ] Wait 30 seconds - your site is live!
- [ ] Copy the temporary URL (e.g., `naisystems-website-abc.vercel.app`)

### 4. Connect Domain (10 minutes)
**In Vercel:**
- [ ] Settings → Domains
- [ ] Add domain: `naisystems.online`
- [ ] Copy the A record IP (e.g., `76.76.21.21`)

**In GoDaddy:**
- [ ] My Products → Domains → naisystems.online → Manage DNS
- [ ] Add A Record:
  - Type: `A`
  - Name: `@`
  - Value: (paste Vercel IP)
  - TTL: 600
- [ ] Add A Record for www:
  - Type: `A`
  - Name: `www`
  - Value: (same Vercel IP)
  - TTL: 600
- [ ] Save

### 5. Set Up Email (5 minutes)
**In GoDaddy:**
- [ ] Email → Email Forwarding
- [ ] Forward: `contact@naisystems.online`
- [ ] To: Your personal email
- [ ] Save and verify

### 6. Wait & Test (10-60 minutes)
- [ ] DNS propagation takes 10-60 minutes
- [ ] Check status: dnschecker.org
- [ ] Once live, test:
  - [ ] https://naisystems.online loads
  - [ ] All pages work
  - [ ] Mobile responsive
  - [ ] Green padlock (SSL)
  - [ ] Email forwarding works

---

## 🎉 Success!

**Your website is live at:** https://naisystems.online

**What's working:**
- ✅ Professional corporate presence
- ✅ Portfolio showcase
- ✅ Clear pricing structure
- ✅ Contact form
- ✅ Auto-deployment (push to GitHub = instant updates)
- ✅ Free SSL certificate
- ✅ Global CDN (fast worldwide)

---

## 📝 Post-Launch Checklist

### Immediate (Today)
- [ ] Send test email to contact@naisystems.online
- [ ] Share site with Daniel for feedback
- [ ] Test on mobile device
- [ ] Verify all links work

### This Week
- [ ] Set up Google Analytics (optional)
- [ ] Submit to Google Search Console
- [ ] Share site on social media
- [ ] Add site to business cards/signatures

### Ongoing
- [ ] Update portfolio as projects complete
- [ ] Monitor contact form submissions
- [ ] Track visitor analytics
- [ ] Iterate on content based on feedback

---

## 🛠️ Making Updates

**To update the website:**
1. Edit files locally
2. Run:
   ```bash
   git add .
   git commit -m "What you changed"
   git push
   ```
3. Vercel auto-deploys in 30 seconds!

**Or ask Niles:**
- Message me with requested changes
- I'll commit and push
- Auto-deploy happens automatically

---

## ❓ Need Help?

**Stuck on a step?**
- Check `DEPLOYMENT-GUIDE.md` for detailed instructions
- Message Niles in Discord #niles-planning
- Vercel support docs: vercel.com/docs

---

**Estimated total time:** 30-40 minutes  
**Most of that is waiting for DNS propagation!**

Let's get this live! 🦞
