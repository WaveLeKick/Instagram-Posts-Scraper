[Instagram Posts Scraper](https://apify.com/instaprism/instagram-posts-scraper?fpr=data)

# Instagram Posts Scraper - Export Posts with Engagement Metrics 2026

Extract posts from any public Instagram account with complete engagement data. Get likes, comments, video views, timestamps, and calculate engagement rates for competitor analysis and content research.

## No Login Required

**Your Instagram account stays safe.** This Actor:

- Does NOT require your Instagram login or cookies
- Uses our own infrastructure to fetch data
- Zero risk of account suspension for you
- Works with any public Instagram profile

Unlike browser extensions or tools that use your account, we handle all scraping server-side. Your credentials are never needed.

## Important: Processing Time

**This Actor uses a distributed scraping architecture.** Here's what to expect:

| Data Size | First Results | Complete Results |
| --- | --- | --- |
| 50 posts | 2-3 min | 3-5 min |
| 200 posts | 3-5 min | 5-10 min |
| 500+ posts | 5-10 min | 10-20 min |

**Why does it take time?**

- Instagram has strict rate limits to prevent spam
- We use multiple proxy servers worldwide to stay undetected
- Each post requires fetching detailed engagement data

**Don't worry about timeouts!** Our streaming mode saves results every 60 seconds. Even if Apify times out after 24h, you'll have all the data collected up to that point.

## What You Get

- **Post URL** - Direct link to the Instagram post
- **Post ID** - Unique identifier for the post
- **Likes Count** - Number of likes on the post
- **Comments Count** - Number of comments
- **Video Views** - View count for videos/reels (null for photos)
- **Media Type** - Photo, video, or carousel
- **Timestamp** - When the post was published
- **Engagement** - Combined likes + comments
- **Caption** - Post text content (when available)

## Input

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `username` | String | Yes | - | The Instagram username to scrape posts from (without the @ symbol) |
| `limit` | Integer | No | 50 | Maximum number of posts to extract. Instagram shows up to ~1000 recent posts |

### Example Input

```
{
    "username": "nike",
    "limit": 100
}
```

## Output

| Field | Type | Example | Description |
| --- | --- | --- | --- |
| `position` | Integer | 1 | Position in the posts feed (1 = most recent) |
| `postId` | String | "3214567890123456789" | Unique Instagram post ID |
| `url` | String | "[https://instagram.com/p/ABC123/](https://instagram.com/p/ABC123/)" | Direct URL to the post |
| `likes` | Integer | 125000 | Number of likes |
| `comments` | Integer | 3500 | Number of comments |
| `engagement` | Integer | 128500 | Total engagement (likes + comments) |
| `timestamp` | String | "2026-01-15T10:30:00.000Z" | When the post was published |
| `mediaType` | String | "video" | Type: "photo", "video", or "carousel" |
| `videoViews` | Integer | 2500000 | View count for videos (null for photos) |
| `scrapedFrom` | String | "nike" | Source account username |
| `scrapedAt` | String | "2026-01-15T12:00:00.000Z" | When the data was scraped |

### Example Output

```
[
    {
        "position": 1,
        "postId": "3214567890123456789",
        "url": "https://www.instagram.com/p/ABC123/",
        "likes": 125000,
        "comments": 3500,
        "engagement": 128500,
        "timestamp": "2026-01-15T10:30:00.000Z",
        "mediaType": "video",
        "videoViews": 2500000,
        "scrapedFrom": "nike",
        "scrapedAt": "2026-01-15T12:00:00.000Z"
    },
    {
        "position": 2,
        "postId": "3214567890123456788",
        "url": "https://www.instagram.com/p/XYZ789/",
        "likes": 89000,
        "comments": 1200,
        "engagement": 90200,
        "timestamp": "2026-01-14T15:00:00.000Z",
        "mediaType": "photo",
        "videoViews": null,
        "scrapedFrom": "nike",
        "scrapedAt": "2026-01-15T12:00:01.000Z"
    }
]
```

## Use Cases

- **Competitor Analysis** - Track what content performs best for your competitors. Identify trends in their top posts.
- **Influencer Vetting** - Verify real engagement rates before signing partnerships. Spot accounts with fake engagement.
- **Content Research** - Analyze what works in your niche. Find the best posting formats and times.
- **Engagement Benchmarking** - Calculate average engagement rates to set realistic KPIs.
- **Trend Detection** - Find viral content patterns by analyzing high-performing posts.

## Streaming Mode (Auto-Save)

This Actor uses **streaming mode** to protect your data:

- Results saved to dataset every 60 seconds
- No data loss even on timeout or interruption
- Monitor progress in real-time via logs
- Partial results always available

## Integrations

Export your data to:

- **Google Sheets** - Direct integration, auto-sync results
- **Zapier / Make (Integromat)** - Trigger workflows when scrape completes
- **Webhooks** - Get real-time notifications
- **API** - Programmatic access via Apify API
- **Download** - JSON / CSV / Excel files

## FAQ

### Why is my scrape taking so long?

Instagram limits how fast data can be fetched. Our distributed architecture uses multiple proxies worldwide to maximize speed while staying undetected. Each post requires individual engagement data fetching.

### Can I scrape private accounts?

No, this Actor only works with public Instagram profiles. Private accounts require login credentials which we don't support.

### What if the Actor times out?

Your data is safe! Streaming mode saves results every 60 seconds to the Apify dataset. If the run times out, you can download whatever was collected.

### How do I calculate engagement rate?

Engagement rate = (likes + comments) / followers * 100. You'll need to combine this data with follower count from our Profile Scraper.

### Can I get the post captions/text?

Caption extraction depends on Instagram's response. When available, captions are included in the output.

### What's the maximum posts I can scrape?

Instagram typically allows access to the most recent ~1000 posts. Older posts may not be accessible via the public API.

### How accurate is the engagement data?

Data is scraped in real-time directly from Instagram. It reflects the current state at scrape time. Note that engagement numbers can change as posts get more likes/comments.

### How often can I run this?

As often as you need. Each run is independent. For tracking changes over time, set up scheduled runs via Apify.

## Keywords

Instagram posts scraper, export Instagram posts, Instagram engagement scraper, scrape Instagram posts, Instagram content analysis, Instagram competitor analysis, Instagram influencer verification, Instagram engagement metrics, export posts to CSV, Instagram data extraction, Instagram likes scraper, Instagram comments scraper

## Need Custom Solutions?

Looking for **custom scraping**, **higher limits**, or **dedicated infrastructure**?

📩 **Contact us:**

- **Telegram:** [@taskforceorange](https://t.me/taskforceorange)
- **Website:** [social-swarm.com](https://social-swarm.com)

We offer:

- Custom actor development
- Enterprise-grade scraping solutions
- Dedicated proxy infrastructure
- White-label integrations
- Priority support

---

*Built with ❤️ by the InstaPrism team*