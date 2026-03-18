---
title: How to Add Google Ads to Your Website
date: 2026-03-19 12:00:00 +0800
categories: [Monetization, Blogging]
tags: [google ads, google adsense, website monetization, seo, jekyll, chirpy]
description: A step-by-step guide to adding Google Ads to your website, including AdSense setup, ads.txt, Chirpy and Jekyll integration, and tips to increase revenue.
---

# How to Add Google Ads to Your Website: A Step-by-Step Guide

Want to monetize your website traffic with Google Ads?

Google AdSense is one of the easiest ways to start earning from a blog, developer site, documentation portal, or niche content website. Whether you run a static site with Jekyll and Chirpy, a personal blog, or a content site with growing search traffic, this guide will show you how to add Google Ads to your website correctly.

This tutorial covers:

- how to apply for Google AdSense
- where to place the AdSense verification code
- how to create and verify `ads.txt`
- how to enable Auto Ads
- how much a technical blog can realistically earn
- common mistakes that can hurt approval or revenue

If you are looking for a beginner-friendly but practical AdSense tutorial, this is the guide to follow.

## What Is Google AdSense?

Google AdSense is Google's website monetization platform. It allows publishers to display ads on their websites and earn revenue from impressions and clicks.

For most small and medium-sized websites, AdSense is the easiest way to start monetizing because:

- it is simple to set up
- it works with content websites and blogs
- you do not need to negotiate with advertisers directly
- Google automatically serves ads relevant to your visitors

If your website gets search traffic, especially from high-value topics like software, AI, SaaS, cloud computing, finance, or productivity, AdSense can become a meaningful source of passive income over time.

## Who Should Add Google Ads to a Website?

Google Ads are a good fit if your site is:

- a personal blog
- a technical blog
- a tutorial website
- a niche media site
- a documentation-heavy content site
- a developer-focused resource hub

AdSense is usually less effective on websites with very little traffic, very thin content, or poor user experience.

## Requirements Before Applying for AdSense

Before you submit your site to Google AdSense, make sure you have the basics covered.

### 1. Publish enough original content

A site with only one or two pages is much less likely to get approved. A safer starting point is:

- at least 5 to 10 solid articles
- original writing
- useful content that solves real problems

For a technical blog, tutorials, troubleshooting articles, tool comparisons, and deep dives usually work well.

### 2. Use a clean and usable layout

Your site should be easy to navigate. It should not feel broken, unfinished, or stuffed with placeholders.

At minimum, make sure you have:

- a homepage
- article pages
- working navigation
- no obvious layout bugs
- no spammy popups

### 3. Add trust pages

These are not always strictly required, but they help:

- About page
- Contact page
- Privacy Policy

If you want to maximize your approval odds, these pages are worth adding.

### 4. Use your own domain if possible

A custom domain generally looks more trustworthy than a temporary subdomain.

### 5. Avoid policy problems

Your site should not contain:

- copied content
- scraped content
- low-quality AI spam
- prohibited topics under AdSense policy

## Step 1: Sign Up for Google AdSense

Go to the AdSense website and submit your site.

Basic process:

1. Open the AdSense signup page.
2. Enter your website URL.
3. Sign in with your Google account.
4. Choose your payment country or region.
5. Submit your site for review.

After that, Google will give you a piece of verification code.

## Step 2: Add the AdSense Verification Code to Your Website

Google usually gives you a script like this:

```html
<script async
  src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXX"
  crossorigin="anonymous"></script>
```

This code serves two purposes:

- it helps verify site ownership for AdSense
- it loads the AdSense library for ad delivery

### Where should you place the AdSense code?

Place it inside the HTML `<head>` section of your site.

If you are using a custom website or framework, add it to the global head template.

### If you use Jekyll and Chirpy

This is important.

Do **not** create or replace `_includes/head.html` with only the AdSense script. Doing that can override the theme's full head template and break CSS and JavaScript loading.

A safer way with Chirpy is to use:

```text
_includes/metadata-hook.html
```

Then add your AdSense script there.

That lets you inject custom head content without breaking the rest of the theme.

## Step 3: Add ads.txt

`ads.txt` is a small text file that tells ad systems which companies are authorized to sell ads for your site.

For Google AdSense, the file usually looks like this:

```txt
google.com, pub-XXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
```

Replace `pub-XXXXXXXXXXXX` with your actual AdSense publisher ID.

### Where should ads.txt go?

It must be reachable at:

```text
https://yourdomain.com/ads.txt
```

That means the file should be published at the root of your website.

### Example for a Jekyll site

Create a file named:

```text
ads.txt
```

Place it in the project root.

If your Jekyll build does not publish it automatically, make sure it is included in the site output.

## Step 4: Verify That ads.txt Works

After deployment, open this URL in your browser:

```text
https://yourdomain.com/ads.txt
```

If everything is correct, you should see only the text content of the file.

If you get a 404 page, then the file is not being published to the root correctly.

## Step 5: Enable Auto Ads

Once your site is connected in AdSense, you can enable Auto Ads.

Auto Ads allows Google to automatically place ads in positions like:

- in-page ads
- anchor ads
- multiplex ads
- vignette ads

For most beginners, Auto Ads is the best starting point because:

- setup is easy
- you do not need to manually create ad slots
- Google handles placement and optimization

Manual ad placement can come later when your traffic grows and you want more control.

## Step 6: Wait for AdSense Approval

Once you submit your website and add the required code, Google will review the site.

Approval time varies. It can take a few days, and sometimes longer.

While waiting:

- ads may not appear yet
- your dashboard may show pending or under review states
- some settings may be visible even before approval is complete

That is normal.

## How Much Can a Technical Blog Make with Google AdSense?

This is the question most people actually care about.

The realistic answer is: it depends on traffic quality, audience geography, niche, and pageviews.

A rough RPM range for a technical blog is often somewhere around:

- lower-end traffic: about $0.5 to $1.5 per 1000 pageviews
- mixed traffic: about $1 to $3 per 1000 pageviews
- higher-value English-speaking tech traffic: about $3 to $10 or more per 1000 pageviews

### Simple revenue examples

| Monthly pageviews | Estimated AdSense revenue |
| --- | --- |
| 10,000 | $5 to $30 |
| 50,000 | $25 to $150 |
| 100,000 | $50 to $300 |
| 500,000 | $250 to $1,500+ |

For many smaller blogs, AdSense starts small. It becomes more meaningful only when your content consistently brings in search traffic.

## Best Content Types for AdSense on a Technical Blog

If you want higher long-term revenue, publish articles that attract search intent and keep readers on the page.

Strong examples include:

- step-by-step tutorials
- troubleshooting guides
- comparison articles
- tool setup guides
- beginner-to-advanced explainers
- performance optimization posts
- deployment and debugging walkthroughs

These tend to perform well because they:

- rank in search
- solve a specific problem
- attract repeatable traffic
- keep readers engaged for longer

## How to Increase AdSense Revenue Without Ruining UX

A lot of publishers make the mistake of chasing short-term ad density and end up harming the site experience.

A better strategy is:

### 1. Publish more search-focused content

Write articles around queries people are already searching for, such as:

- how to fix something
- how to set up a tool
- best alternatives for a product
- comparison guides

### 2. Improve time on page

Keep readers engaged by using:

- clear headings
- code examples
- screenshots
- concise explanations
- internal links to related posts

### 3. Target high-value niches

Topics like these often monetize better:

- AI tools
- SaaS
- cloud services
- developer tooling
- business software
- productivity workflows

### 4. Combine AdSense with affiliate content

For many technical blogs, affiliate links can eventually outperform AdSense.

For example, if you review tools, hosting providers, developer products, or SaaS services, affiliate revenue can be much stronger than ad revenue alone.

## Common AdSense Mistakes to Avoid

Here are some of the most common issues:

### Breaking the site theme when adding code

If you use Jekyll or a theme framework, do not override core theme files carelessly.

### Missing `ads.txt`

This can lead to revenue warnings and prevent full monetization efficiency.

### Applying too early

If your site has almost no content, approval is harder.

### Publishing low-quality filler content

Thin content hurts both SEO and AdSense trust.

### Focusing only on ads instead of traffic

AdSense income comes from traffic. Better content and better SEO usually matter more than ad placement tweaks at the beginning.

## Final Thoughts

Adding Google Ads to your website is one of the simplest ways to start monetizing a content site.

If you are using Jekyll, Chirpy, GitHub Pages, or another static setup, the process is still very manageable:

1. apply for AdSense
2. add the AdSense script to your site head
3. publish `ads.txt`
4. enable Auto Ads
5. wait for approval
6. keep publishing useful content

For a technical blog, the real long-term opportunity is not just adding ads. It is building high-quality content that ranks in search, earns trust, and compounds over time.

If your site is growing, AdSense can be a good first monetization layer. Later, you can combine it with affiliate links, sponsored placements, digital products, or your own tools.

## FAQ

### Can I add Google AdSense to a static website?

Yes. Static websites can use AdSense as long as you can add the required script to the page head and publish `ads.txt` at the root.

### Does Chirpy support Google AdSense?

Yes. Chirpy can support AdSense, but you should avoid overriding `_includes/head.html` with a minimal file. Using `_includes/metadata-hook.html` is safer for custom head injections.

### Is Auto Ads enough for a beginner?

Yes. Auto Ads is usually the simplest and best starting point. Manual ad slots can come later.

### How long does AdSense approval take?

It varies. Many sites are reviewed within days, but some take longer.

### How much traffic do I need to make money with AdSense?

You can technically earn with low traffic, but meaningful revenue usually requires consistent search traffic and a growing content base.
