# Facebook Scraper API: How to Pull Public Facebook Data Without Meta's App Review — ScraperAPI Plans, Real Credit Costs, and Which Tier to Pick

If you searched for a **facebook scraper api**, you probably already ran into the wall that is Meta's official offering. The Graph API only reads Pages you administer, getting an app through review is its own project, and Page access tokens are a whole separate headache. Third-party scraper APIs skip all of that. Some, like Bright Data or Refetcher, sell Facebook-specific endpoints that return ready-parsed JSON. ScraperAPI takes a different route: it's a general-purpose scraping API that fetches any URL, including Facebook pages, through rotating residential proxies with JavaScript rendering and CAPTCHA handling built in, and you parse the HTML yourself.

Which route makes sense depends on your project. This article covers both, then digs into ScraperAPI's actual plans, what a Facebook request really costs in credits, and what happens when you run out, details most comparison posts skip.

> **Quick picks, if you don't want to read all of it:**
> - Just evaluating? The free plan gives 1,000 credits every month with up to 5 concurrent connections, and your first 7 days include 5,000 extra credits. No credit card needed for the trial.
> - Small side project: Hobby at $49/month, or $44.10 on annual billing, covers 100,000 credits and 20 concurrent requests.
> - Production workload: Scaling at $475/month ($427.50 annual) is the most popular tier and the cheapest one that includes pay-as-you-go.
> - 👉 [See ScraperAPI's current plans and prices](https://www.scraperapi.com/pricing?fp_ref=coupons)

## Why the official Graph API won't get you there

Meta's Graph API is designed for page owners. You register a developer app, pass review, obtain a Page access token, and you can read data for Pages you administer. For public Pages you don't own, it's largely a dead end, which is exactly why the third-party scraper market exists.

One more thing worth knowing before you buy anything: Facebook gates a lot of content behind login for logged-out visitors. Groups, events, Marketplace, and comments often require an authenticated session even for dedicated scraper services. Public Pages, posts, and the Ad Library are the reliably accessible targets. If your use case is group or Marketplace data, check any provider's docs carefully before paying.

## Dedicated Facebook APIs vs general scraping APIs

The "facebook scraper api" market splits into two camps, and mixing them up leads to bad purchases.

**Dedicated Facebook APIs** return structured, Facebook-shaped JSON. You send a page URL or post ID, you get followers, captions, reaction counts, comment trees, whatever that provider supports. Bright Data's Facebook scraper works this way, billed per successful record with a free tier of 5,000 records per month, sync requests capped at 20 URLs, and async jobs accepting up to 1 GB of input with delivery to S3, Snowflake, and similar targets. Refetcher and ScrapeBadger take the same approach; ScrapeBadger covers Marketplace listings and the Ad Library, though its global keyword search was temporarily unavailable as of its latest docs. One specialist service bills roughly $0.60 per 1,000 requests on its Pro tier, with pay-as-you-go top-ups at $0.90 per 1,000 successful requests and a median response time around 2.6 seconds.

**General scraping APIs** like ScraperAPI don't sell Facebook-specific endpoints. They solve the harder underlying problem: getting the page at all. Rotating residential and mobile IPs, JavaScript rendering, CAPTCHA and anti-bot detection, automatic retries, custom sessions and headers. You receive the raw page and write your own parser. The trade-off is more work on your side; the payoff is one subscription that also covers every other site in your pipeline, from e-commerce to search results.

| Service | Approach | What you actually get | Pricing starting point |
| --- | --- | --- | --- |
| Bright Data | Dedicated Facebook API | Parsed records per page/post, async jobs, S3/Snowflake delivery | Pay per successful record; 5K records/month free |
| Refetcher | Dedicated Facebook API | Posts, Reels, videos, profiles with detailed metric fields | Per-request pricing |
| ScrapeBadger | Dedicated Facebook API | Marketplace, Pages, groups, posts, comments, Ad Library as JSON | Per-request pricing |
| ScraperAPI | General scraping API | Raw HTML from any URL with proxies, JS rendering, CAPTCHA bypass | Free plan; paid tiers from $49/month |

If all you ever need is Facebook data in clean JSON, a dedicated API is the shorter path. If your workload touches multiple sites, or you already have parsing code, ScraperAPI's single subscription tends to be the simpler setup.

## ScraperAPI plans and pricing

ScraperAPI's pricing page currently shows seven paid tiers plus a free plan. All paid plans include the same core feature set: JavaScript rendering, premium residential and mobile IPs, JSON auto-parsing for supported domains, rotating proxy pools, CAPTCHA and anti-bot detection, custom sessions, custom headers, desktop and mobile user agents, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Support is the same across tiers too: priority support, a dedicated support team, and Slack support.

Annual billing takes 10% off. The table shows both prices.

| Plan | Monthly price | Annual (per month) | Credits/month | Concurrent requests | Purchase |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [ Get Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [ Get Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [ Get Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [ Get Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons&plan=scaling) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [ Get Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [ Get Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | [ Talk to Sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

The free plan sits below all of this: 1,000 credits per month with up to 5 concurrent connections, available indefinitely for small projects. The documentation also lists a Student plan, though it isn't priced on the public pricing page, so you'd check the dashboard for that.

A couple of differences between tiers don't show up in the price column. **Geotargeting on Hobby and Startup is limited to US and EU locations**; country-level targeting starts at Business. The analytics dashboard on Hobby and Startup only keeps the last 30 days of data, while Business and up have no limit. Those two restrictions are the real reason to jump from Startup to Business if you're scraping from specific countries or need longer usage history.

On the annual math: Hobby costs $588 billed monthly versus $529.20 annually, a saving of $58.80 per year. Scaling is $5,700 versus $5,130, saving $570. The 10% applies uniformly, so if you're committed for a year, annual billing is strictly better.

## What a Facebook scrape actually costs in credits

Here's the part most comparison articles gloss over: ScraperAPI doesn't bill a flat one-credit-per-request rate. A standard page costs 1 credit, but some sites have custom pricing because they're harder to scrape. Amazon costs 5 credits per request, Google and Bing (including subdomains) cost 25, and LinkedIn costs 30. Sites behind Cloudflare, Datadome, or PerimeterX protection add 10 credits per request when the bypass kicks in.

Facebook isn't on the published list of specially priced domains, which means it should fall under standard pricing. That said, actual consumption depends on the parameters you use and how Facebook serves the page at any given moment. Two tools exist precisely for this:

1. The **Domain Cost Estimator** in your dashboard shows the exact per-request cost for any URL before you run volume.
2. The **`max_cost` parameter** lets you cap any single request, so one expensive scrape can't quietly eat a chunk of your monthly allowance.

Do this before committing to a plan: run the estimator on a few representative Facebook URLs, multiply by your expected volume, and match the result to the credit tiers above. A Hobby plan's 100,000 credits covers 100,000 standard pages, but only 10,000 pages if your targets somehow bill at 10 credits each. Thirty seconds of math beats a surprise mid-month pause.

## What happens when you run out of credits

By default, scraping stops when your credits run out, and it stays stopped until the next billing cycle. That default catches people off guard during a production run, so it's worth knowing your three options.

**Auto-upgrade** is opt-in and available on Hobby through Professional. When credits run out, your account moves to the next tier automatically, usually at a better per-credit price. Useful if you'd rather not think about it, risky if you'd rather not pay it.

**Pay-as-you-go** keeps you on your current plan and continues scraping at a fixed per-credit rate, available on Scaling, Professional, Advanced, and Enterprise. You can set a monthly spending cap, and the service won't exceed it unless you change the setting yourself. It's a limit, not a pre-charge.

**Early renewal** applies to annual plans: you can re-subscribe before the year ends to get a fresh batch of credits.

Concurrency works differently. If you fire more requests than your plan allows, the API returns a 429 and turns the request away rather than queuing it, and there's no charge for the rejected request. Your code just needs to back off and retry.

## Free trial, refund policy, and cancelling

The risk of trying this is low. The 7-day trial includes 5,000 credits and doesn't require a credit card. After that, the free plan keeps 1,000 credits per month flowing for as long as you want, which is enough to properly test Facebook scraping at small scale before paying anything.

If you do pay and change your mind, ScraperAPI offers a **7-day no-questions-asked refund**. Contact support and they process it. Cancelling a subscription is a self-service action in the dashboard with no cancellation fee, and you can change your card details anytime on the billing page.

👉 [Start the 7-day free trial with 5,000 credits](https://www.scraperapi.com/pricing?fp_ref=coupons) if you want to test against your actual target pages before deciding on a tier.

## Which plan fits your project

The tier boundaries map cleanly onto real situations:

- **Evaluating feasibility**: free plan. 1,000 credits per month plus the 5,000 trial credits will tell you whether Facebook pages come back cleanly with JS rendering and residential IPs.
- **Side project or personal tooling, under 100K pages/month**: Hobby. At $44.10 annually it's the cheapest paid entry, and 20 concurrent requests is plenty for a single-user tool.
- **Roughly 1M pages/month**: Startup. Same US/EU geotargeting limit as Hobby, so only choose this over Business if location doesn't matter to you.
- **Production with country-specific targeting, or you need full analytics history**: Business. The $150 jump from Startup buys country-level geotargeting and unlimited dashboard history.
- **5M+ pages and you want a spending-capped buffer for spikes**: Scaling. It's the most popular tier for a reason, and it's the floor for pay-as-you-go. 👉 [Check the Scaling plan here](https://www.scraperapi.com/pricing?fp_ref=coupons&plan=scaling).
- **10M+ pages or multi-source data pipelines**: Professional or Advanced, depending on whether 10.5M or 21.5M credits matches your volume.
- **22M+ requests a month**: Enterprise, priced custom through sales.

One honest caveat: if your project consists entirely of pulling structured Facebook JSON and you have no interest in writing a parser, a dedicated Facebook API will be less work end to end, and a couple of them have cheaper entry points for low volume. ScraperAPI earns its keep when Facebook is one stop among several in your pipeline, when you need the same infrastructure for e-commerce, search, and social data, or when you already maintain parsing code.

## Frequently asked questions

**Does ScraperAPI return parsed Facebook JSON?**
No. It returns the raw page HTML. Its auto-parsing and structured data features apply to domains where ScraperAPI maintains parsing templates, and Facebook isn't one of them. You supply the parser, which also means you control exactly which fields you keep.

**Do I need a Facebook account or session cookies?**
For public Pages and posts, the API requests pages the way a logged-out visitor would, through residential IPs. Content Facebook gates behind login, such as many groups, events, and Marketplace listings, isn't reachable without handling authentication yourself, and this limitation applies to dedicated Facebook APIs as well.

**What happens if I exceed my plan's concurrency limit?**
The API returns a 429 response and discards the request without charging a credit. Reduce concurrent requests or add retry logic with backoff.

**Is there a refund if the service doesn't work for my use case?**
Yes, a 7-day no-questions-asked refund, handled through support. Combined with the no-card 7-day trial and the permanent free plan, you can validate Facebook scraping thoroughly before any money is committed.

## Before you subscribe

Match the plan to your measured numbers, not to the "Most popular" badge. Run the Domain Cost Estimator on your real Facebook URLs, confirm the per-request credit cost, and size the tier from there. If you're still unsure between two tiers, start lower and switch on auto-upgrade, since upgrading is allowed at any time from the billing page.

👉 [Compare all ScraperAPI plans and grab the free trial](https://www.scraperapi.com/pricing?fp_ref=coupons) to get your 5,000 test credits and see how your target pages behave before paying for anything.
