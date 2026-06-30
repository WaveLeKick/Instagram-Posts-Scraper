[Instagram Posts Scraper](https://apify.com/goat255/instagram-posts-scraper?fpr=data)

# Instagram Posts Scraper

Scrape Instagram posts in bulk with full captions, engagement metrics, media URLs, locations, tagged users, and carousel data. Handles pagination automatically.

## What it does

- Scrapes **post data** — captions, like/comment counts, video views, media URLs, timestamps
- Extracts **media details** — images, videos, carousels with all child slides
- Captures **metadata** — locations, tagged users, coauthors, paid partnership flags
- Accepts **usernames, @handles, or full Instagram URLs** — mix and match any format
- Handles **pagination** automatically — set how many posts you want and it fetches across as many pages as needed
- Runs **multiple usernames in parallel** with configurable concurrency
- Uses **multiple independent sources** with automatic failover
- Returns **one flat JSON object per post** — each post includes a `username` field so you can easily group and filter results by account

## Output

Each result is one JSON object per post. Every post includes the `username` field, so when scraping multiple accounts you can **group results by username** to see each account's posts separately.

| Field | Type | Description |
| --- | --- | --- |
| `username` | string | Username this post belongs to — use this to group posts by account |
| `id` | string | Post ID |
| `shortcode` | string | URL slug (`instagram.com/p/{shortcode}`) |
| `mediaType` | string | `"image"`, `"video"`, or `"carousel"` |
| `timestamp` | integer | When posted (unix timestamp) |
| `caption` | string | Full caption text |
| `displayUrl` | string | Main image URL |
| `thumbnailUrl` | string | Square thumbnail URL |
| `videoUrl` | string | Video URL (if video) |
| `dimensions` | object | `{"height": 1080, "width": 1080}` |
| `accessibilityCaption` | string | Alt text |
| `likeCount` | integer | Number of likes |
| `commentCount` | integer | Number of comments |
| `videoViewCount` | integer | Video views (if video) |
| `location` | string | Location name |
| `taggedUsers` | string[] | Tagged usernames |
| `coauthors` | string[] | Collab post co-authors |
| `isPaidPartnership` | boolean | Sponsored content flag |
| `commentsDisabled` | boolean | Comments turned off |
| `children` | object[] | Carousel slides (each with `id`, `mediaType`, `displayUrl`, `videoUrl`, `dimensions`) |

## Use cases

- **Content analysis** — analyze captions, hashtags, and posting patterns at scale
- **Engagement tracking** — monitor likes, comments, and video views across accounts
- **Competitor monitoring** — track what competitors post, how often, and engagement rates
- **Influencer analytics** — evaluate content performance for influencer vetting
- **Brand monitoring** — find posts mentioning your brand via tagged users and coauthors

## Integrations

### Apify API

```
# Get all posts
curl "https://api.apify.com/v2/datasets/{DATASET_ID}/items?format=json"

# Filter posts by username using the API
curl "https://api.apify.com/v2/datasets/{DATASET_ID}/items?format=json&fields=username,shortcode,likeCount,caption"
```

### Python

```
from apify_client import ApifyClient
from itertools import groupby
from operator import itemgetter

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("YOUR_ACTOR_ID").call(run_input={
    "usernames": ["nasa", "spacex"],
    "maxPostsPerUser": 24,
})

# Group posts by username
posts = list(client.dataset(run["defaultDatasetId"]).iterate_items())
posts.sort(key=itemgetter("username"))

for username, user_posts in groupby(posts, key=itemgetter("username")):
    user_posts = list(user_posts)
    avg_likes = sum(p.get("likeCount", 0) or 0 for p in user_posts) / len(user_posts)
    print(f"@{username}: {len(user_posts)} posts, avg {avg_likes:.0f} likes")
```

### JavaScript / Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('YOUR_ACTOR_ID').call({
    usernames: ['nasa', 'spacex'],
    maxPostsPerUser: 24,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();

// Group posts by username
const grouped = Object.groupBy(items, post => post.username);
for (const [username, posts] of Object.entries(grouped)) {
    const avgLikes = posts.reduce((sum, p) => sum + (p.likeCount || 0), 0) / posts.length;
    console.log(`@${username}: ${posts.length} posts, avg ${Math.round(avgLikes)} likes`);
}
```

### Webhooks & other platforms

Use [Apify integrations](https://docs.apify.com/platform/integrations) to send results to Google Sheets, Slack, Zapier, Make, Amazon S3, or your own webhook endpoint.

## Pricing

This actor uses **pay-per-event** pricing. You are charged per post successfully scraped. Check the Pricing tab for current rates.

## Proxy requirements

**Residential proxies are required.** Configured by default with Apify's residential proxy pool.

## Limits

- **Private accounts**: Posts are not accessible for private accounts
- **Post pagination**: Each page returns ~12 posts. Fetching 100 posts requires ~9 pages
- **Rate limits**: Use `delayBetweenRequests` (default 1s) and reasonable `concurrency` (default 5)