[Instagram Posts Scraper](https://apify.com/khadinakbar/instagram-posts-scraper?fpr=data)

# 🔥 Instagram Posts Scraper – Profiles, Hashtags & URLs

> Extract Instagram posts from any combination of profiles, hashtags, and direct post URLs — all in one actor. No login required. Returns captions, engagement metrics, media URLs, location, tagged users, and more.

---

## What does Instagram Posts Scraper do?

Instagram Posts Scraper is a powerful, multi-input actor that extracts structured post data from Instagram's public pages. Unlike other scrapers that force you to use separate tools for profiles vs. hashtags, this actor handles all three input types in a single run: **usernames**, **hashtags**, and **direct post URLs**.

Feed it a mix of inputs and get back clean, structured JSON with everything you need — captions, hashtags, engagement metrics, media URLs, location tags, co-authors, tagged users, and optional recent comments.

---

## Why use Instagram Posts Scraper?

- **All-in-one input** — scrape profile posts, hashtag feeds, and specific post URLs in one run
- **Rich data output** — 30+ fields including accessibility captions, co-authors, tagged users, and pinned/sponsored flags that basic scrapers miss
- **Date filtering** — skip posts older than a specified date without wasting credit
- **No login required** — works entirely on public Instagram data
- **MCP & AI ready** — semantic field names and rich schema for seamless integration with Claude, ChatGPT, and other AI workflows
- **Competitive pricing** — $0.0012/post on free tier, down to $0.0003 at Diamond

---

## What data can Instagram Posts Scraper extract?

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | Instagram internal post ID |
| `shortcode` | string | Shortcode used in the post URL |
| `url` | string | Direct link to the post |
| `post_type` | string | IMAGE, VIDEO, CAROUSEL_ALBUM, or REEL |
| `caption` | string | Full caption text |
| `hashtags` | array | Extracted hashtags (no # symbol) |
| `mentions` | array | Extracted @mentions |
| `accessibility_caption` | string | AI-generated image alt text |
| `like_count` | integer | Number of likes |
| `comment_count` | integer | Number of comments |
| `video_view_count` | integer | Views (videos/reels only) |
| `video_play_count` | integer | Plays (videos/reels only) |
| `video_duration` | number | Duration in seconds |
| `thumbnail_url` | string | Main post thumbnail |
| `display_url` | string | Full resolution image URL |
| `media_urls` | array | All images in a carousel |
| `video_url` | string | Direct video file URL |
| `owner_username` | string | Post author's username |
| `owner_full_name` | string | Post author's display name |
| `owner_is_verified` | boolean | Verified badge status |
| `owner_follower_count` | integer | Author's follower count |
| `location_name` | string | Tagged location |
| `location_id` | string | Instagram location ID |
| `tagged_users` | array | Users tagged in the post |
| `coauthors` | array | Collaboration co-author usernames |
| `is_pinned` | boolean | Whether the post is pinned |
| `is_sponsored` | boolean | Paid partnership flag |
| `is_reel` | boolean | Whether it's a Reel |
| `comments_disabled` | boolean | Whether comments are off |
| `timestamp` | string | Post publish date (ISO 8601) |
| `scraped_at` | string | Scrape timestamp (ISO 8601) |
| `recent_comments` | array | Up to 5 recent comments with text, username, timestamp, likes |

---

## How to use Instagram Posts Scraper

### Step 1 — Choose your input type

You can mix and match all three input types in a single run:

**By username (profile posts):**

```
natgeo
nasa
https://www.instagram.com/natgeo/
```

**By hashtag:**

```
travel
#photography
nature
```

**By direct post URL:**

```
https://www.instagram.com/p/CxABCde1234/
https://www.instagram.com/reel/CxABCde5678/
```

### Step 2 — Set your limits

- **Max Posts Per Target** — How many posts to fetch per profile or hashtag (default: 50, max: 500)
- **Only Posts Newer Than** — Skip old posts. Accepts `YYYY-MM-DD` or relative values like `7 days`, `2 months`, `1 year`

### Step 3 — Run and export

Click **Start** and your data will appear in the **Output** tab. Export as JSON, CSV, or Excel.

### API usage example

```
const { ApifyClient } = require('apify-client');

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('khadinakbar/instagram-posts-scraper').call({
    instagramUsernames: ['natgeo', 'nasa'],
    hashtags: ['photography'],
    maxPostsPerTarget: 100,
    onlyPostsNewerThan: '30 days',
    includeRecentComments: true,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(`Scraped ${items.length} posts`);
```

---

## Pricing

This actor uses **Pay Per Event** pricing — you only pay for posts that are successfully scraped.

| Plan | Price Per Post |
| --- | --- |
| Free | $0.0012 |
| Bronze | $0.0010 |
| Silver | $0.0009 |
| Gold | $0.0007 |
| Platinum | $0.0005 |
| Diamond | $0.0003 |

**Example cost:** Scraping 1,000 posts on a free plan = **$1.20**

There is also a small actor start fee of $0.00005 per run.

---

## Use cases

**Social media analytics** — Track posting frequency, engagement trends, and content format performance across competitor profiles.

**Influencer research** — Identify high-performing creators in a niche by scraping hashtag posts and sorting by engagement rate.

**Brand monitoring** — Monitor @mentions and brand hashtags to discover user-generated content and brand conversations.

**Content strategy** — Analyze which post types (image, reel, carousel) get the most engagement in your niche.

**Market research** — Scrape posts from industry accounts and hashtags to identify trends and content gaps.

**Lead generation** — Extract public contact info and profile data from business accounts in your target market.

**AI training data** — Collect captioned images with accessibility_caption fields for computer vision and NLP model training.

**Competitive intelligence** — Monitor competitor brands' posting schedules, hashtag strategies, and engagement patterns.

---

## Frequently asked questions

**Does it require Instagram login?**
No. This scraper only collects publicly available data from Instagram's public pages. No login credentials are required.

**Why do some posts have null values?**
Instagram doesn't always return every field for every post, especially video view counts for older content. Missing values are returned as `null` rather than empty strings.

**Can I scrape private accounts?**
No. Only public Instagram profiles and posts are accessible without login.

**What proxies does it use?**
The actor uses Apify's residential proxy pool by default, which is recommended for Instagram. Datacenter proxies are frequently blocked by Instagram's bot detection.

**Can I schedule automatic runs?**
Yes — use Apify Scheduler to run the actor on any schedule (daily, weekly, etc.) and save your results to a dataset for trend analysis.

**Why am I getting fewer posts than expected?**
Instagram limits how many posts are visible on public pages without authentication. The practical limit is typically 50-200 posts per profile scroll. For comprehensive historical data, consider multiple scheduled runs.

**Does it work with Instagram Reels?**
Yes. Reels are returned with `post_type: "REEL"` and `is_reel: true`, including view counts and video duration.

---

## Other actors you might find useful

- [Instagram Hashtag Scraper](https://apify.com/apify/instagram-hashtag-scraper) — Dedicated hashtag scraper from Apify
- [Instagram Profile Scraper](https://apify.com/apify/instagram-profile-scraper) — Scrape profile-level info (bio, followers, following)
- [Instagram Comments Scraper](https://apify.com/apify/instagram-comment-scraper) — Deep comment extraction for sentiment analysis

---

## Legal disclaimer

This actor is designed for collecting publicly available data from Instagram in compliance with applicable laws. Users are solely responsible for ensuring their use complies with Instagram's Terms of Service, applicable privacy laws (including GDPR and CCPA), and any other relevant regulations. The actor author does not endorse or encourage any use that violates these terms. Data collected should not be used to harass, spam, or target individuals without their consent.

Export scraped data, run the scraper via API, schedule and monitor runs, or integrate with other tools and AI workflows.