# 💡 Analyst Memo — Shopify App Store Insights

**Dashboard:** Shopify App Store Analysis
**Reporting Period:** Latest available data (2018–2024)

---

## Key Insight

The Shopify App Store marketplace is in a strong growth phase: review activity across all 500 apps is up **91.09% year-over-year**, with an average customer rating of **4.19 out of 5** across roughly 8,000 reviews. The **SEO** category generates more reviews than any other category in the marketplace, making it the current center of gravity for merchant engagement. Review volume also follows a consistent seasonal pattern — activity peaks sharply every December before dropping off in January — suggesting merchants engage most heavily with apps around year-end business cycles (likely tied to holiday sales prep and year-end store optimization) before tapering into the new year.

One area with clear room for improvement: developers reply to only **24.80%** of customer reviews. With review volume growing this quickly, that reply rate will only become a larger gap if it isn't addressed.

## Business Impact

- **Growth is broad-based, not a fluke.** A 91% YoY increase in review volume across the full app catalog signals genuine rising merchant engagement with the App Store, not a one-off spike in a single category.
- **SEO's lead position matters for merchandising and partner strategy.** Since SEO apps draw the most review activity, they're likely also driving discovery and installs — the category deserves prioritized placement, curation, and possibly closer partnership support from Shopify's team.
- **The December spike / January drop is a predictable, repeatable pattern.** This is valuable for planning — marketplace campaigns, featured app placements, or developer outreach initiatives timed around Q4 will land when merchant attention is naturally highest.
- **Low developer reply rates are a merchant satisfaction risk.** A quarter of reviews getting a developer response means most customer feedback — positive or negative — currently goes unacknowledged. As review volume keeps climbing, unanswered reviews (especially negative ones) become more visible and can quietly erode trust in the marketplace.

## Recommendation

1. **Double down on the SEO category.** Investigate what's driving SEO's outsized review volume — pricing model, feature set, or something else — and evaluate whether promoting similar app types across other categories replicates that engagement.
2. **Plan Q4 marketplace initiatives around the December peak.** Time developer outreach programs, featured app promotions, or App Store campaigns to land in November/December when merchant attention and review activity are naturally at their highest.
3. **Set a developer reply-rate target.** Consider surfacing reply rate as a visible metric to developers (e.g., in their partner dashboard) and encourage a response benchmark — even a modest increase from 24.80% toward 40–50% would materially improve merchant-facing engagement as review volume continues to grow.
4. **Monitor the January drop-off.** Confirm whether this is purely seasonal (expected, low-risk) or indicates a post-holiday support gap worth addressing with merchants.

---

## Dashboard Contents

**Overview page:** high-level KPIs (Total Apps, Total Reviews, Average Rating, Developer Reply %), category and free-plan filters, and a category breakdown of review volume.

**Trend Analysis page:** review activity over time, year-over-year comparisons, and running (YTD) totals, built using DAX time intelligence functions (`CALCULATE`, `SAMEPERIODLASTYEAR`, `DATEADD`, `TOTALYTD`).

## Data Model

Star schema with `dim_date` (calendar table) connected to both `apps` (via `launch_date`) and `reviews` (via `posted_at`), with `apps` and `reviews` joined on `app_id`. See `screenshots/model_view.png`.

## Data Sources

- `data/apps.csv` — 500 Shopify apps: name, developer, category, launch date, pricing.
- `data/reviews.csv` — customer reviews: rating, post date, developer reply flag, helpful count.

Both files were cleaned in Power Query: trimmed text fields, standardized category capitalization, removed duplicate reviews, filtered invalid ratings (outside 1–5), standardized mixed date formats, and converted the developer-reply flag to a numeric 1/0 field for KPI calculations.
