[Instagram Posts Scraper](https://apify.com/vulnv/instagram-posts-scraper?fpr=data)

## Overview

The **Instagram Posts Scraper** is an Apify Actor that extracts detailed data from **Instagram posts** at scale. Perfect for content creators, social media marketers, influencer researchers, and brand analysts — with **no Instagram login, cookies, or browser automation required**.

✅ No Instagram login required | ✅ Bulk post processing | ✅ Structured JSON output | ✅ High success rate

---

### **Complete Post Data**

- **Media Information** — Photos, videos, thumbnail, carousel content (post_content), alt text, shortcode
- **Engagement Metrics** — Likes, comments count
- **Content Details** — Description/caption, hashtags, content type (Image/Video/Carousel)
- **Creator Details** — Username, user ID, profile image, follower count, posts count, verified status, profile URL
- **Partnership Info** — Paid partnership status and details
- **Metadata** — Post date, post ID, content ID, audio, video duration, timestamp

### **Key Features**

- **No Authentication Required** — Works without Instagram cookies or login
- **Bulk Processing** — Handle multiple post URLs in one run
- **Clean JSON Output** — Structured, ready-to-use data format
- **Real-time Processing** — Monitor extraction progress
- **High Reliability** — Built-in retry mechanisms and error handling

---

## 🧾 Input Configuration

Submit an array of Instagram Post URLs via Apify's input:

```
{
  "urls": [
    "https://www.instagram.com/p/Cuf4s0MNqNr",
    "https://www.instagram.com/p/DP861NijuwE"
  ]
}
```

---

## 📤 Output Format

Each post will return detailed data such as:

```
{
  "url": "https://www.instagram.com/p/DP861NijuwE",
  "user_posted": "amyclaireboutique",
  "description": "✨ The ultimate outfit finisher! A scarf instantly elevates any look. 🌸\nBecause when in doubt… just add a scarf. 💕\n\n🛍️ Shop at @amyclaireboutique link in bio!\n#amyclaireboutique #stylemadeeasy #scarfstyle #boutiqueaccessories #fallfashion",
  "hashtags": [
    "#amyclaireboutique",
    "#stylemadeeasy",
    "#scarfstyle",
    "#boutiqueaccessories",
    "#fallfashion"
  ],
  "num_comments": 0,
  "date_posted": "2025-10-18T13:14:07.000Z",
  "likes": 7,
  "photos": ["https://scontent.cdninstagram.com/..."],
  "post_id": "3746127733433756676",
  "shortcode": "DP861NijuwE",
  "content_type": "Image",
  "pk": "3746127733433756676",
  "content_id": "DP861NijuwE",
  "thumbnail": "https://scontent.cdninstagram.com/...",
  "followers": 321,
  "posts_count": 105,
  "profile_image_link": "https://scontent.cdninstagram.com/...",
  "is_verified": false,
  "is_paid_partnership": false,
  "partnership_details": null,
  "user_posted_id": "77561612778",
  "post_content": [
    {
      "index": 0,
      "type": "Photo",
      "url": "https://scontent.cdninstagram.com/...",
      "id": "3746127733433756676",
      "alt_text": "Photo by Amy Claire Boutique on October 18, 2025."
    }
  ],
  "audio": null,
  "profile_url": "https://www.instagram.com/amyclaireboutique",
  "videos_duration": null,
  "images": [],
  "alt_text": "Photo by Amy Claire Boutique on October 18, 2025.",
  "photos_number": 0,
  "timestamp": "2026-02-22T19:47:07.423Z",
  "input": {
    "url": "https://www.instagram.com/p/DP861NijuwE"
  }
}
```

> **Note:** The exact output fields depend on the data available for each post. Some fields like `audio` or `videos_duration` may be `null` for image-only posts. Long CDN URLs are truncated above for readability.

---

## 📊 Output & Export

### **Dataset Storage**

- All extracted data is stored in your Apify dataset
- Each post becomes one dataset item
- Failed extractions are logged with error details

### **Export Formats**

- **JSON** — Raw structured data for API integration
- **CSV** — Spreadsheet-compatible format
- **Excel** — Formatted spreadsheet with multiple sheets

---

## 💼 Common Use Cases

### **Content Strategy & Trend Analysis**

- Analyze trending post formats, hashtags, and content types
- Study viral content patterns and engagement drivers
- Research optimal posting times and caption strategies

### **Influencer Marketing & Research**

- Evaluate influencer post performance and engagement rates
- Compare content quality across potential brand ambassadors
- Track sponsored post metrics and ROI

### **Competitive Analysis**

- Monitor competitor post strategies and performance
- Benchmark engagement metrics against industry standards
- Identify successful content themes in your niche

### **Brand Monitoring**

- Track brand mentions and tagged posts
- Analyze user-generated content and sentiment
- Monitor campaign hashtag performance

### **Academic & Market Research**

- Study social media content trends at scale
- Analyze visual content engagement patterns
- Research platform-specific content performance

---

## ✅ Example Use

```
{
  "urls": [
    "https://www.instagram.com/p/Cuf4s0MNqNr",
    "https://www.instagram.com/p/DP861NijuwE"
  ]
}
```

After execution, the dataset will contain detailed data for each Instagram post including media URLs, engagement metrics, creator information, comments, and more.

## 🔗 Related Scrapers

Check out these other scrapers from [Vulnv on Apify](https://apify.com/vulnv):

| Scraper | Description |
| --- | --- |
| [Instagram Profile Scraper](https://apify.com/vulnv/instagram-profile-scraper) | Extract profile data, follower counts, bio, posts, and engagement metrics from public Instagram profiles |
| [Instagram Reels Scraper](https://apify.com/vulnv/instagram-reels-scraper) | Extract video data, engagement metrics, and audio info from Instagram Reels |
| [Facebook Profile Scraper](https://apify.com/vulnv/facebook-profile-scraper) | Scrape public Facebook profile information and post data |
| [TikTok Scraper](https://apify.com/vulnv/tiktok-scraper) | Extract video data, engagement metrics, and creator info from TikTok |
| [LinkedIn Profile Scraper](https://apify.com/vulnv/linkedin-profile-scraper) | Scrape public LinkedIn profile data without login |
| [LinkedIn Posts Scraper](https://apify.com/vulnv/linkedin-posts-scraper) | Extract LinkedIn post content, engagement metrics, and comments |
| [Reddit Posts Scraper](https://apify.com/vulnv/reddit-posts-scraper) | Collect Reddit posts and comments from any subreddit |

🔍 Explore the full collection at 🌐 [Vulnv's Apify Actors](https://apify.com/vulnv)

📧 For support or collaborations, reach out at [apify@vulnv.com](mailto:apify@vulnv.com).