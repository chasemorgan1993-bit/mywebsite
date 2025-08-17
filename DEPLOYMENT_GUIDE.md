# Hugo Site Deployment Guide: GitHub + Netlify

This guide will walk you through deploying your TheMerchantGuide Hugo site using GitHub for version control and Netlify for hosting.

## 📋 Prerequisites

- [GitHub account](https://github.com)
- [Netlify account](https://netlify.com) 
- Git installed on your computer
- Hugo site ready for deployment (✅ Done!)

## 🚀 Step-by-Step Deployment

### Phase 1: Prepare Your Site for Deployment

#### 1.1 Build and Test Locally
```bash
# Make sure you're in your Hugo site directory
cd /Users/chasemorgan/themerchantguide

# Test the build process
hugo --gc --minify

# Verify the site works
hugo server
# Check http://localhost:1313
```

#### 1.2 Verify Configuration Files
✅ **Already Created:**
- `netlify.toml` - Netlify build configuration
- `.gitignore` - Files to exclude from Git
- `README.md` - Project documentation

---

### Phase 2: Create GitHub Repository

#### 2.1 Initialize Git Repository (if not done)
```bash
# Navigate to your site directory
cd /Users/chasemorgan/themerchantguide

# Check if git is already initialized
git status

# If not initialized, run:
# git init
```

#### 2.2 Create Repository on GitHub
1. Go to [GitHub.com](https://github.com)
2. Click **"New repository"** (green button)
3. **Repository name**: `themerchantguide`
4. **Description**: "Payment processor finder tool for small businesses"
5. **Visibility**: Public (recommended) or Private
6. **DO NOT** initialize with README (we have our own)
7. Click **"Create repository"**

#### 2.3 Connect Local Repository to GitHub
```bash
# Add all files to git
git add .

# Create initial commit
git commit -m "Initial commit: Hugo site with payment processor finder

🧭 Features:
- Interactive payment processor recommendation tool
- Fee calculator for cost comparisons
- Blog section with payment processing guides
- Professional design with cohesive color system
- Mobile responsive layout

🎨 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"

# Add GitHub repository as remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/themerchantguide.git

# Push to GitHub
git push -u origin main
```

---

### Phase 3: Deploy to Netlify

#### 3.1 Connect Netlify to GitHub

1. **Go to [Netlify.com](https://netlify.com)**
2. **Sign up/Log in** (use GitHub account for easier integration)
3. **Click "Add new site"** → **"Import an existing project"**
4. **Choose "Deploy with GitHub"**
5. **Authorize Netlify** to access your GitHub account
6. **Select your repository**: `themerchantguide`

#### 3.2 Configure Build Settings

Netlify should auto-detect Hugo, but verify these settings:

**Build Settings:**
- **Base directory**: (leave empty)
- **Build command**: `hugo --gc --minify`
- **Publish directory**: `public`
- **Functions directory**: (leave empty)

**Advanced Settings:**
- **HUGO_VERSION**: `0.148.2`
- **HUGO_ENV**: `production`

#### 3.3 Deploy Your Site

1. **Click "Deploy site"**
2. **Wait for build** (usually 1-3 minutes)
3. **Check build logs** if there are issues
4. **Your site is live!** (temporary URL like `amazing-unicorn-123456.netlify.app`)

---

### Phase 4: Configure Custom Domain (Optional)

#### 4.1 Set Up Custom Domain
1. **In Netlify dashboard**, go to **Site settings**
2. **Click "Domain management"**
3. **Add custom domain**: `themerchantguide.com`
4. **Follow DNS instructions** from your domain provider

#### 4.2 Enable HTTPS
1. **In Domain settings**, scroll to **HTTPS**
2. **Enable "Force HTTPS"**
3. **Netlify automatically provides SSL certificate**

---

### Phase 5: Set Up Continuous Deployment

#### 5.1 Automatic Deployments (Already Configured!)
- ✅ **Push to `main` branch** → Auto-deploy
- ✅ **Pull requests** → Deploy preview
- ✅ **Branch deploys** → Test features

#### 5.2 Deploy Contexts
```toml
# netlify.toml already configured for:
- Production builds (main branch)
- Deploy previews (pull requests)  
- Branch deploys (feature branches)
```

---

## 🔧 Common Commands

### Local Development
```bash
# Start development server
hugo server

# Build for production
hugo --gc --minify

# Create new blog post
hugo new content/blog/my-new-post.md
```

### Git Workflow
```bash
# Check status
git status

# Add changes
git add .

# Commit changes
git commit -m "Add new blog post about Square vs Stripe"

# Push to GitHub (triggers Netlify build)
git push
```

### Netlify CLI (Optional)
```bash
# Install Netlify CLI
npm install -g netlify-cli

# Login to Netlify
netlify login

# Deploy from local
netlify deploy

# Deploy to production
netlify deploy --prod
```

---

## 🐛 Troubleshooting

### Build Failures

**Hugo version mismatch:**
```bash
# Check your local Hugo version
hugo version

# Update netlify.toml if needed
[build.environment]
  HUGO_VERSION = "0.148.2"  # Match your local version
```

**CSS/JS not loading:**
- Check file paths in templates
- Verify files are in `static/` directory
- Check browser console for errors

**Form not working:**
- Verify JavaScript syntax
- Check browser developer tools
- Test locally first

### Git Issues

**Large files:**
```bash
# Remove large files from git history
git rm --cached large-file.png
echo "large-file.png" >> .gitignore
git commit -m "Remove large file"
```

**Merge conflicts:**
```bash
# Pull latest changes
git pull origin main

# Resolve conflicts in files
# Then commit
git add .
git commit -m "Resolve merge conflicts"
git push
```

---

## 📊 Site Performance

### Optimization Tips
- ✅ **Hugo minification** (already enabled)
- ✅ **Netlify compression** (automatic)
- ✅ **CDN delivery** (Netlify global CDN)
- ✅ **Caching headers** (configured in netlify.toml)

### Monitoring
- **Netlify Analytics** (built-in)
- **Google Analytics** (add to templates if needed)
- **Core Web Vitals** (test with PageSpeed Insights)

---

## 🔐 Security

### Already Configured
- ✅ **Security headers** (XSS, CSRF protection)
- ✅ **HTTPS redirect** 
- ✅ **Content Security Policy**

### Additional Security
- **Environment variables** for sensitive data
- **Form spam protection** (Netlify built-in)
- **Branch protection** (GitHub settings)

---

## 🎯 Next Steps After Deployment

1. **Test all functionality** on live site
2. **Set up Google Analytics** (if needed)
3. **Configure contact forms** (if needed)
4. **Add site to Google Search Console**
5. **Create social media cards** (meta tags)
6. **Set up monitoring** (uptime checks)

---

## 📞 Support Resources

- **Hugo Documentation**: https://gohugo.io/documentation/
- **Netlify Documentation**: https://docs.netlify.com/
- **GitHub Documentation**: https://docs.github.com/

---

## ✅ Deployment Checklist

### Pre-Deployment
- [ ] Site builds successfully locally (`hugo --gc --minify`)
- [ ] All pages load correctly in browser
- [ ] Forms and interactive elements work
- [ ] Mobile responsive design verified
- [ ] Content is finalized and reviewed

### GitHub Setup
- [ ] Repository created on GitHub
- [ ] Local repository connected to GitHub
- [ ] Initial commit pushed to main branch
- [ ] README.md and documentation added

### Netlify Configuration  
- [ ] Netlify account connected to GitHub
- [ ] Repository imported to Netlify
- [ ] Build settings configured correctly
- [ ] First deployment successful
- [ ] Custom domain configured (if applicable)

### Post-Deployment
- [ ] Live site tested thoroughly
- [ ] All links working correctly
- [ ] Forms submitting properly
- [ ] Analytics set up (if needed)
- [ ] SEO basics in place
- [ ] Performance optimized

Your Hugo site is now ready for deployment! 🚀