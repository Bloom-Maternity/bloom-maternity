# Bloom Maternity - Deployment Guide

## What you need
- A GitHub account (free)
- A Cloudflare account (free)
- Access to your Netregistry DNS settings for bloommaternity.com.au

## Step 1: Create a GitHub account
1. Go to github.com and sign up with your email
2. Choose the free plan

## Step 2: Create a repository
1. Click the "+" icon in the top right, then "New repository"
2. Name it: bloom-maternity
3. Set it to Public (required for free Cloudflare Pages)
4. Click "Create repository"

## Step 3: Upload the site files
1. On your new repo page, click "uploading an existing file"
2. Drag the entire bloom-maternity folder contents into the upload area
3. Keep the folder structure intact (blog/, css/, maternity-dresses/, etc.)
4. Click "Commit changes"

Alternatively, if you install Git on your computer:
```
cd bloom-maternity
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/YOUR-USERNAME/bloom-maternity.git
git push -u origin main
```

## Step 4: Connect Cloudflare Pages
1. Go to dash.cloudflare.com and create a free account
2. In the sidebar, click "Workers & Pages"
3. Click "Create" then "Pages" tab
4. Click "Connect to Git"
5. Authorise Cloudflare to access your GitHub
6. Select the bloom-maternity repository
7. Build settings:
   - Framework preset: None
   - Build command: (leave empty)
   - Build output directory: /
8. Click "Save and Deploy"

Your site will be live at bloom-maternity.pages.dev within minutes.

## Step 5: Add your custom domain
1. In Cloudflare Pages, go to your bloom-maternity project
2. Click "Custom domains" tab
3. Click "Set up a custom domain"
4. Enter: bloommaternity.com.au
5. Also add: www.bloommaternity.com.au
6. Cloudflare will give you two nameservers (e.g., anna.ns.cloudflare.com)

## Step 6: Update Netregistry DNS
1. Log into your Netregistry account
2. Go to Domain Management for bloommaternity.com.au
3. Find "Nameservers" or "DNS Settings"
4. Replace the existing nameservers with the two Cloudflare gave you
5. Save changes
6. Wait 24-48 hours for DNS to propagate

## Step 7: SSL Certificate
Cloudflare will automatically provision a free SSL certificate. Your site will be accessible via https://bloommaternity.com.au once DNS propagates.

## Ongoing: Adding new content
The daily scheduled task in Claude generates new blog posts. To publish them:

**Option A (manual):** Download the generated HTML files and upload them to your GitHub repo via the web interface.

**Option B (automated via Git):** If you set up Git locally, you can pull the generated files and push to GitHub. Each push auto-deploys to Cloudflare Pages.

## Site structure
```
bloom-maternity/
  index.html                          (homepage)
  css/style.css                       (site styles)
  robots.txt                          (search engine directives)
  sitemap.xml                         (search engine sitemap)
  _headers                            (Cloudflare security/cache headers)
  _redirects                          (URL redirects)
  maternity-dresses/index.html        (category page)
  maternity-workwear/index.html       (category page)
  maternity-casual/index.html         (category page)
  maternity-occasion-wear/index.html  (category page)
  blog/index.html                     (blog listing)
  blog/best-maternity-dresses-australia/index.html
  blog/maternity-workwear-guide/index.html
  blog/summer-maternity-outfits-australia/index.html
```

## After launch checklist
- [ ] Submit sitemap to Google Search Console (google.com/webmasters)
- [ ] Verify site in Google Search Console
- [ ] Set up Google Analytics (optional but recommended)
- [ ] Create social media accounts (Instagram, Pinterest)
- [ ] Submit site to Australian business directories
