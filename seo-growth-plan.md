# Days at the Office — SEO Growth Plan

## Current Situation
- ~25 downloads/month, 0 Pro conversions
- Apple Ads: $250 spent, 97% wasted on irrelevant Search Match terms (Piggly Wiggly, Duck Life, Jiffy Lube, etc.)
- Website exists at daysattheoffice.com but **not indexed by Google**
- 5 free tool pages already built (great foundation)
- Direct competitors: "Hybrid Office Tracker" (iOS/Android), "In The Office Tracker" (macOS), "Days In Office" (daysinoffice.com)

## The Opportunity
RTO is the biggest workplace story of 2025-2026. Companies are mandating 3-5 days/week. 69% now measure compliance (up from 45%). Employees are anxious about tracking their own attendance. Yet almost nobody is creating content for the **individual worker** trying to track their own days. Enterprise tools (Envoy, Robin, Archie) target HR/admins. Your app targets the employee — and that's an uncontested content niche.

---

## PHASE 0: Local Development Setup (Day 1)

**You need a local copy of the site so you can make changes, preview them, and push updates.**

### 0A. Clone the Repo
```bash
cd ~/Projects   # or wherever you keep projects

# Replace with your actual repo URL
git clone https://github.com/YOUR_USERNAME/daysattheoffice.git
cd daysattheoffice
```

### 0B. Preview Locally
Since it's plain HTML, no build step needed. Just open files in your browser:
```bash
# Option 1: Open directly
open index.html

# Option 2: Run a simple local server (better for testing relative links)
# If you have Python installed:
python3 -m http.server 8000
# Then visit http://localhost:8000
```
- [ ] Verify homepage and all 5 tool pages load correctly

### 0C. Create the Blog Structure
```bash
# Create the blog directory
mkdir -p blog/how-to-track-office-days

# Copy the blog post HTML I provided into it
cp ~/Downloads/blog-post-1-how-to-track-office-days.html blog/how-to-track-office-days/index.html
```
- [ ] Open `blog/how-to-track-office-days/index.html` and replace the nav placeholder at the top with your actual site nav/header
- [ ] Update any relative links (CSS, images) to work from the `/blog/` subdirectory
- [ ] Preview locally to make sure it looks right

### 0D. Add a Sitemap (Critical for Google Indexing)
Create a `sitemap.xml` in your repo root:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://daysattheoffice.com/</loc><priority>1.0</priority></url>
  <url><loc>https://daysattheoffice.com/tools/commute-cost-calculator/</loc></url>
  <url><loc>https://daysattheoffice.com/tools/return-to-office-cost-calculator/</loc></url>
  <url><loc>https://daysattheoffice.com/tools/office-attendance-percentage-calculator/</loc></url>
  <url><loc>https://daysattheoffice.com/tools/hybrid-work-schedule-generator/</loc></url>
  <url><loc>https://daysattheoffice.com/tools/best-days-to-go-into-the-office/</loc></url>
  <url><loc>https://daysattheoffice.com/blog/how-to-track-office-days/</loc></url>
</urlset>
```
Add new URLs to this file every time you publish a new blog post.

### 0E. Add robots.txt
Create a `robots.txt` in your repo root:
```
User-agent: *
Allow: /
Sitemap: https://daysattheoffice.com/sitemap.xml
```

### 0F. Push and Verify
```bash
git add .
git commit -m "Add blog post, sitemap, and robots.txt"
git push origin main
```
- [ ] Wait 1-2 minutes for GitHub Pages to deploy
- [ ] Verify https://daysattheoffice.com/sitemap.xml loads
- [ ] Verify https://daysattheoffice.com/robots.txt loads
- [ ] Verify https://daysattheoffice.com/blog/how-to-track-office-days/ loads

**Once this is done, move straight to Phase 1A — submitting to Google Search Console.**

---

## PHASE 1: Get Found (Week 1-2)

### 1A. Get Indexed by Google
**Priority: CRITICAL — nothing else matters until this is done**

- [ ] Create a Google Search Console account at search.google.com/search-console
- [ ] Verify ownership of daysattheoffice.com (DNS TXT record or HTML file method)
- [ ] Submit sitemap.xml (ensure your site generator creates one, or create manually)
- [ ] Request indexing of your homepage and all tool pages
- [ ] Create a Bing Webmaster Tools account and submit there too
- [ ] Ensure robots.txt allows crawling

### 1B. Fix On-Page SEO Basics
- [ ] Add unique `<title>` and `<meta description>` tags to every page
  - Homepage: "Days at the Office — Automatic Office Day Tracker for Hybrid Workers"
  - Each tool page needs its own unique title targeting its keyword
- [ ] Add Open Graph tags for social sharing
- [ ] Ensure all pages have proper H1 → H2 → H3 hierarchy
- [ ] Add alt text to all images
- [ ] Ensure mobile-friendly (test with Google's Mobile-Friendly Test)
- [ ] Check page speed (target < 3 seconds load time)

### 1C. Pause Apple Ads
- [ ] Pause the Discovery campaign immediately (stop the bleeding)
- [ ] Keep Brand campaign running at $5/day (it's cheap and protective)
- [ ] Do NOT restart paid ads until organic funnel is working

---

## PHASE 2: Content That Ranks (Week 2-4)

### 2A. Blog Posts (Publish 1 per week)

**Post 1: "How to Track Your Office Days in 2026: The Complete Guide for Hybrid Workers"**
- Target keywords: "track office days," "office day tracker," "hybrid work tracker"
- Angle: Overview of methods (spreadsheet, calendar, apps), then position your app as the automatic solution
- Include: comparison table, screenshots, download CTA
- Word count: 1,500-2,000

**Post 2: "RTO Compliance: How to Prove You Were in the Office"**
- Target keywords: "prove office attendance," "RTO compliance tracking," "office attendance proof"
- Angle: With 69% of companies now measuring compliance, employees need their own records
- Include: Why you need your own records (HR systems can be wrong), how GPS-based tracking works
- Tie-in: Privacy angle — your records, on your device, not your employer's surveillance tool

**Post 3: "The Hidden Costs of Going Back to the Office (And How to Calculate Them)"**
- Target keywords: "cost of going to office," "RTO cost calculator," "commute cost hybrid work"
- Angle: Link to your existing Commute Cost Calculator and RTO Cost Calculator tools
- Include: Statistics on commute costs, childcare, wardrobe, meals
- This post is a traffic magnet that funnels to your tools

**Post 4: "Best Days to Go Into the Office in 2026 (Data-Backed Guide)"**
- Target keywords: "best days to go to office," "busiest office days," "when to go to office hybrid"
- Angle: Tuesday-Thursday are peak; link to your existing "Best Office Days" tool
- Include: Survey data, tips for optimizing in-office time

**Post 5: "Days at the Office vs. Manual Tracking: Why Automatic Beats Spreadsheets"**
- Target keywords: "office attendance tracker app," "automatic office day tracker"
- Angle: Direct comparison — spreadsheets vs. calendar blocking vs. your app
- Bottom-of-funnel conversion content

### 2B. Optimize Existing Tool Pages
Each of your 5 tool pages should have:
- [ ] 300-500 words of helpful context ABOVE the tool (what it does, why it matters, how to use it)
- [ ] 200-300 words BELOW the tool (related tips, link to blog posts, CTA to download app)
- [ ] Unique title tag targeting the tool's primary keyword
- [ ] Internal links to related blog posts and other tools
- [ ] Schema markup (FAQ schema if applicable)

---

## PHASE 3: Build Authority (Week 3-6)

### 3A. Directory & Listing Submissions
- [ ] Submit to ProductHunt (plan a proper launch — teaser, hunter, launch day)
- [ ] Submit to AlternativeTo.net (list as alternative to Envoy, Robin, Hubstaff)
- [ ] Submit to SaaSHub
- [ ] Submit to AppSumo marketplace (even just for visibility)
- [ ] Submit to BetaList
- [ ] Create a listing on Capterra / G2 / GetApp (free tiers available)

### 3B. Community Engagement (Ongoing)
Reddit posts (genuine, not spammy):
- [ ] r/hybridwork — "I built an app to automatically track my office days"
- [ ] r/remotework — Share your RTO cost calculator as a free tool
- [ ] r/SideProject — Launch story
- [ ] r/iOSProgramming — Technical deep dive on geofencing
- [ ] r/apple — If relevant thread appears about hybrid work

LinkedIn content:
- [ ] Post 1: "I tracked my office days for 6 months. Here's what I learned." (personal story)
- [ ] Post 2: Share RTO statistics + link to your calculator
- [ ] Post 3: "Why I built a privacy-first alternative to employer surveillance tools"
- [ ] Post 4: Comment on trending RTO news with your perspective

### 3C. Backlink Building
- [ ] Reach out to blogs writing "best hybrid work tools" listicles — pitch inclusion
- [ ] HARO/Connectively — sign up as a source for hybrid work topics
- [ ] Guest post on productivity or HR blogs (offer your RTO data/calculator as value)

---

## PHASE 4: Convert Visitors (Week 4-8)

### 4A. Website Conversion Optimization
- [ ] Add email capture (newsletter or "Get hybrid work tips") — builds an audience you own
- [ ] Add social proof: testimonials, download count, App Store rating
- [ ] Add a "Why Privacy Matters" section — this is your #1 differentiator
- [ ] Consider adding a blog sidebar CTA that follows on scroll

### 4B. App Store Optimization (ASO)
- [ ] Rewrite App Store description with keyword-rich copy
- [ ] Redo screenshots to be benefit-driven, not feature-driven
  - "Never Manually Track Office Days Again" > "Calendar View"
  - "Prove You Were There — Automatically" > "Visit History"
  - "Your Data. Your Device. Your Privacy." > "Privacy First"
- [ ] Add an App Preview video (screen recording with captions)
- [ ] Update subtitle: "Auto-Track Your Hybrid Office Days"
- [ ] Optimize keyword field (100 characters — use every one)

### 4C. Fix the Pro Conversion Path
- [ ] Ensure free users get value within first 5 minutes (first tracked visit = activation)
- [ ] Consider: make the free tier more generous temporarily to build habit and reviews
- [ ] Add a soft paywall prompt after 2 weeks of active use, not immediately
- [ ] Show "You've been in the office X days this month" push notification — builds habit

---

## Measurement & Timeline

| Metric | Now | 30 Days | 90 Days | Goal |
|--------|-----|---------|---------|------|
| Google indexed pages | 0 | 6-10 | 15-20 | 20+ |
| Monthly organic visitors | ~0 | 50-100 | 500-1000 | 2000+ |
| Monthly downloads | 25 | 40-60 | 100-200 | 500+ |
| Pro conversions | 0 | 1-3 | 10-20 | 50+ |
| App Store rating count | ? | +5 | +20 | 50+ |
| Domain Authority | 0 | 5-10 | 15-20 | 25+ |

## Budget
- Google Search Console: Free
- Bing Webmaster Tools: Free
- Blog content: Your time (or $50-100/post if outsourced)
- ProductHunt launch: Free
- Reddit/LinkedIn posting: Free
- Email capture tool (Mailchimp/Buttondown): Free tier
- **Total: $0-200/month vs. $250/month wasted on Apple Ads**

---

## Priority Order (What to Do First)

1. **TODAY**: Pause Discovery Apple Ads campaign
2. **TODAY**: Clone the repo locally, get the site running (Phase 0)
3. **THIS WEEK**: Set up Google Search Console, submit sitemap, verify indexing
4. **THIS WEEK**: Create `/blog/` directory, deploy Blog Post #1
5. **NEXT WEEK**: Optimize tool pages with SEO content
6. **NEXT WEEK**: Submit to ProductHunt, AlternativeTo, directories
7. **WEEK 3**: Publish Blog Post #2, start Reddit/LinkedIn engagement
8. **WEEK 4**: Publish Blog Post #3, begin backlink outreach
9. **ONGOING**: 1 blog post per week, 2-3 community posts per week
