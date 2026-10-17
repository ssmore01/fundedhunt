# FundedHunt SEO fix: deploy steps

Put ALL files in this folder in the ROOT of your GitHub repo (ssmore01/fundedhunt), replacing what is there, then push to main.

- index.html (homepage app, now with crawlable article links, one clean schema block, no fake search URL)
- 17 article files (one real page per article: own title, canonical, Article schema, H1, related links)
- sitemap.xml (home + 17 correct URLs)
- robots.txt
- _redirects (replaces the old one; the old catch-all rule is gone)
- 404.html (wrong URLs now return a real 404 instead of the homepage)

If you have an old /blog-posts folder in the repo, delete it. The article files must sit at the root.

## Check after Cloudflare redeploys (2 minutes)
1. Open https://www.fundedhunt.com/how-to-use-prop-firm-payout , View Source: you must see `<link rel="canonical" href="https://www.fundedhunt.com/how-to-use-prop-firm-payout">` and an `<h1>`.
2. Open https://www.fundedhunt.com/this-does-not-exist : must show "Page not found" (not the homepage).
3. Open https://www.fundedhunt.com/blog/how-to-use-prop-firm-payout : must jump to /how-to-use-prop-firm-payout.

## Search Console
1. Sitemaps: remove the old sitemap, add `sitemap.xml`.
2. URL Inspection: paste an article URL, Test Live URL, Request Indexing. Quota is about 10 a day. Start with: prop-firm-scams-red-flags-checklist, how-to-pass-prop-firm-challenge-30-days, how-to-use-prop-firm-payout, liquidity-sweep-grab-trading-guide, best-funded-accounts-indian-traders-2026.
3. Pages > "Crawled - currently not indexed" > Validate Fix.
4. Ignore "Page with redirect" (http to https) and "Alternative page with proper canonical" (non-www, ?q=). Those are normal.
