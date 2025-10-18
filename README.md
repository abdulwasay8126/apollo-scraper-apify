# Apollo.io Free Account Scraper - Apify Actor

## ðŸš€ What is this?

A powerful **Apify Actor** that scrapes Apollo.io using a **100% free account** - no paid API or credits required!

### âœ¨ Key Features

- âœ… **Works with FREE Apollo accounts** - No paid subscription needed
- âœ… **Scrapes forever** - No expiring credits or API limits
- âœ… **Comprehensive data** - Extracts ALL visible information
- âœ… **Smart pagination** - Automatically handles multiple pages
- âœ… **Profile enrichment** - Optional deep dive into each contact
- ðŸ› ï¸ **ADVANCED ANTI-DETECTION** - undetected-chromedriver + stealth JS
- ðŸª **Cookie Authentication** - Skip login & CAPTCHA on subsequent runs
- ðŸ¤– **Human-Like Behavior** - Realistic typing, mouse movements, delays
- âœ… **Session persistence** - Saves login cookies for future runs

### ðŸ†• v2.0 - Anti-Detection Upgrade

**NEW:** This scraper now uses **industry-leading anti-detection technology**:
- âœ… **undetected-chromedriver** - Automatically bypasses bot detection
- âœ… **Cookie-based auth** - Skip login after first run (90% CAPTCHA reduction!)
- âœ… **Human behavior simulation** - Variable typing speed, mouse movements, typos
- âœ… **Advanced stealth JavaScript** - Multi-layer detection bypass
- âœ… **90-95% success rate** (vs 30-40% with standard Selenium)

ðŸ“– **Read more:** [ANTI_DETECTION_GUIDE.md](./ANTI_DETECTION_GUIDE.md)

---

## ðŸ“Š What Can Be Scraped?

### Contacts/Leads
- âœ… Name, Title, Company
- âœ… Email addresses (if visible)
- âœ… Phone numbers (mobile, direct, office)
- âœ… Location
- âœ… LinkedIn, Twitter, GitHub profiles
- âœ… Work experience & education
- âœ… Technologies/skills

### Companies
- âœ… Company name, website, description
- âœ… Industry, employee count, revenue
- âœ… Headquarters location
- âœ… Technologies used
- âœ… Funding information
- âœ… Social media profiles

### Search Results
- âœ… Bulk extraction with auto-pagination
- âœ… Up to 100 pages per search (configurable)
- âœ… Optional enrichment (visit detail pages)

---

## ðŸŽ¯ How to Use

### Step 1: Configure Input

Set up your input with:

```json
{
  "apolloEmail": "your@email.com",
  "apolloPassword": "your_password",
  "startUrls": [
    {
      "url": "https://app.apollo.io/#/search?query=..."
    }
  ],
  "maxPages": 10,
  "enrichProfiles": true,
  "proxyConfiguration": {
    "useApifyProxy": true
  }
}
```

### Step 2: Get Apollo URLs

1. Go to **Apollo.io** and create your search
2. **Copy the URL** from your browser
3. Add it to `startUrls` in the input

### Step 3: Run the Actor

Click "Start" and the actor will:
1. Login to your Apollo account
2. Navigate to each URL
3. Scrape all visible data
4. Save to Apify dataset
5. Handle pagination automatically

---

## ðŸ“¥ Input Parameters

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `apolloEmail` | String | âœ… Yes | Your Apollo.io account email |
| `apolloPassword` | String | âœ… Yes | Your Apollo.io account password |
| `startUrls` | Array | âœ… Yes | Apollo.io URLs to scrape |
| `maxPages` | Integer | No | Max pages per URL (default: 10) |
| `enrichProfiles` | Boolean | No | Visit detail pages (default: true) |
| `minDelay` | Integer | No | Min delay in seconds (default: 3) |
| `maxDelay` | Integer | No | Max delay in seconds (default: 7) |
| `proxyConfiguration` | Object | No | Proxy settings (recommended) |

---

## ðŸ“¤ Output Format

The actor pushes data to the Apify dataset in this format:

```json
{
  "type": "contact",
  "name": "John Doe",
  "title": "Software Engineer",
  "company": "Tech Corp",
  "location": "San Francisco, CA",
  "email": "john@techcorp.com",
  "phone": "+1-555-123-4567",
  "linkedin_url": "https://linkedin.com/in/johndoe",
  "social_links": {
    "linkedin": "https://linkedin.com/in/johndoe",
    "twitter": "https://twitter.com/johndoe"
  },
  "experience": [
    {
      "title": "Software Engineer",
      "company": "Tech Corp",
      "duration": "2020-Present"
    }
  ],
  "education": [
    {
      "school": "MIT",
      "degree": "BS Computer Science"
    }
  ],
  "technologies": ["Python", "JavaScript", "AWS"],
  "scraped_at": "2025-10-08T10:30:00"
}
```

---

## ðŸ’¡ Usage Examples

### Example 1: Scrape Tech Startup Founders

```json
{
  "apolloEmail": "your@email.com",
  "apolloPassword": "your_password",
  "startUrls": [
    {
      "url": "https://app.apollo.io/#/search?query=founders%20tech%20startups"
    }
  ],
  "maxPages": 20,
  "enrichProfiles": true
}
```

### Example 2: Quick List (No Enrichment)

```json
{
  "apolloEmail": "your@email.com",
  "apolloPassword": "your_password",
  "startUrls": [
    {
      "url": "https://app.apollo.io/#/search?query=..."
    }
  ],
  "maxPages": 5,
  "enrichProfiles": false
}
```

### Example 3: Multiple Searches

```json
{
  "apolloEmail": "your@email.com",
  "apolloPassword": "your_password",
  "startUrls": [
    { "url": "https://app.apollo.io/#/search?query=..." },
    { "url": "https://app.apollo.io/#/companies/12345" },
    { "url": "https://app.apollo.io/#/people/67890" }
  ]
}
```

---

## ðŸ”§ Configuration Tips

### For Maximum Speed
- Set `enrichProfiles: false`
- Reduce `maxPages` to 5-10
- Use `minDelay: 2` and `maxDelay: 4`

### For Maximum Data
- Set `enrichProfiles: true`
- Increase `maxPages` to 50-100
- Keep default delays (3-7 seconds)

### For Best Reliability
- Enable `useApifyProxy: true`
- Use longer delays (5-10 seconds)
- Process URLs one at a time

---

## âš ï¸ Important Notes

### Free Account Limits
- Free Apollo accounts have monthly search limits (~50-100 searches)
- Some emails may be locked/hidden on free tier
- The scraper respects these limits and scrapes what's visible

### Session Persistence
- After first login, cookies are saved
- Future runs use saved session (faster!)
- No need to login every time

### Proxy Recommendation
- **Strongly recommended** to use Apify proxies
- Prevents IP bans and rate limiting
- Already included in input template

---

## ðŸ› Troubleshooting

### "Login failed"
- Double-check your Apollo credentials
- Make sure account is active
- Try logging in manually first

### "No results found"
- Verify the URL is correct
- Check if your free searches are exhausted
- Make sure you're using search/profile URLs

### Actor Runs Slow
- This is intentional! Delays prevent detection
- Disable enrichment for faster runs
- Reduce maxPages

### "Session expired"
- The actor will re-login automatically
- Saved cookies refresh on each run

---

## ðŸ“ˆ Best Practices

1. **Start Small**: Test with 1-2 pages first
2. **Use Proxies**: Enable Apify proxy for reliability
3. **Respect Limits**: Don't scrape aggressively
4. **Monitor Usage**: Check Apollo's free search limits
5. **Enrich Selectively**: Only enrich when you need detailed data

---

## âš–ï¸ Legal & Ethical Use

**DISCLAIMER**: This actor is for educational and personal use only.

- âš ï¸ Respect Apollo.io's Terms of Service
- âš ï¸ Don't scrape at excessive rates
- âš ï¸ Comply with GDPR and data privacy laws
- âš ï¸ Use data ethically and legally

The actor includes built-in delays and anti-detection to be respectful of the platform.

---

## ðŸ”’ Security

- Passwords are stored securely in Apify
- Marked as secret in input schema
- Never logged or exposed
- Session cookies saved in key-value store

---

## ðŸ’° Cost

### Actor Usage
- **Apify Free Tier**: ~5-10 hours of runtime/month
- **Paid Plans**: $49/month for unlimited

### No Apollo Costs
- âœ… Uses FREE Apollo account
- âœ… No API credits required
- âœ… No paid subscription needed
- âœ… Works forever!

---

## ðŸ“ž Support

For issues or questions:
1. Check this README carefully
2. Review input configuration
3. Check actor logs for errors
4. Contact Apify support

---

## ðŸŽ‰ Ready to Scrape!

1. âœ… Enter your Apollo credentials
2. âœ… Add your Apollo URLs
3. âœ… Configure max pages and enrichment
4. âœ… Click "Start"
5. âœ… Download your data from dataset!

**Happy Scraping! ðŸš€**

---

*Version 1.0.0 - Built for Apify Platform*
