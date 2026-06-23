[Google Maps Lead Scraper](https://apify.com/sovereigntaylor/google-maps-lead-scraper?fpr=data)

Extract business leads from Google Maps with **emails, phone numbers, websites, ratings, and reviews**. The ultimate tool for B2B lead generation, sales prospecting, local marketing, and competitive analysis.

## What Makes This Different

Most Google Maps scrapers give you basic business info. This actor goes **three layers deeper**:

1. **Searches Google Maps** for businesses matching your query with full pagination
2. **Extracts detailed data** from each listing — name, address, phone, rating, reviews, category, hours, price level, coordinates, photos, place ID
3. **Visits business websites** to find email addresses using multiple extraction strategies (mailto links, regex scanning, contact page crawling, meta tag parsing)
4. **Validates and deduplicates** all contact data before output

The result: **sales-ready lead lists** with verified contact information you can import directly into your CRM.

## Use Cases

### Sales & Outreach

- **Cold Email Campaigns** — Build targeted lists of businesses with verified emails for outreach
- **Sales Prospecting** — Find decision-makers at local businesses by industry and location
- **Account-Based Marketing** — Map out all businesses in a target market segment

### Local Marketing & Agencies

- **Client Prospecting** — Find businesses that need marketing services (low ratings, no website, etc.)
- **Competitor Analysis** — Map all competitors in a geographic area with ratings and reviews
- **Local SEO Audits** — Analyze business presence and review profiles across a region

### Market Research

- **Business Density Analysis** — Count and categorize businesses by area and industry
- **Rating & Review Analysis** — Benchmark quality scores across competitors
- **Pricing Intelligence** — Compare price levels across similar businesses
- **New Market Entry** — Evaluate business landscapes before expanding to new cities

### Real Estate & Recruiting

- **Property Management Leads** — Find property managers, real estate agents, brokerages
- **Recruiting Targets** — Identify companies in specific industries for talent sourcing
- **Vendor Discovery** — Find service providers and suppliers in any category

## Input Examples

### Basic - Plumbers in Austin TX

```
{
  "searchQuery": "plumbers in Austin TX",
  "maxResults": 100,
  "includeEmails": true,
  "includePhone": true,
  "includeWebsite": true
}
```

### Targeted - Dentists in Los Angeles

```
{
  "searchQuery": "dentists in Los Angeles CA",
  "maxResults": 500,
  "includeEmails": true,
  "includePhone": true,
  "includeWebsite": true,
  "language": "en"
}
```

### International - Hotels in Paris

```
{
  "searchQuery": "hotels in Paris",
  "location": "Paris, France",
  "maxResults": 300,
  "includeEmails": true,
  "includePhone": true,
  "includeWebsite": true,
  "language": "fr"
}
```

### Budget Run - Quick Sample

```
{
  "searchQuery": "restaurants near downtown Chicago",
  "maxResults": 50,
  "includeEmails": true,
  "includePhone": true,
  "includeWebsite": true
}
```

### Spanish Market

```
{
  "searchQuery": "abogados en Madrid",
  "maxResults": 200,
  "includeEmails": true,
  "includePhone": true,
  "includeWebsite": true,
  "language": "es"
}
```

## Output Format

Each lead in the dataset contains:

| Field | Type | Description |
| --- | --- | --- |
| `businessName` | string | Business name as shown on Google Maps |
| `address` | string | Full street address |
| `phone` | string | Primary phone number |
| `website` | string | Business website URL |
| `email` | string | Primary email address (first found) |
| `allEmails` | array | All email addresses found on the website |
| `rating` | number | Google Maps rating (1.0 - 5.0) |
| `reviewCount` | number | Number of Google reviews |
| `category` | string | Business category (e.g. "Plumber", "Restaurant") |
| `priceLevel` | string | Price level ($, $$, $$$, $$$$) |
| `hours` | object | Operating hours by day of week |
| `latitude` | number | GPS latitude coordinate |
| `longitude` | number | GPS longitude coordinate |
| `placeId` | string | Google Maps Place ID |
| `photos` | array | URLs of business photos |
| `isVerified` | boolean | Whether the business is verified on Google |
| `googleMapsUrl` | string | Direct link to Google Maps listing |
| `emailSources` | array | Where each email was found (mailto, regex, contact-page) |
| `socialLinks` | object | Social media profiles found on the website |
| `leadScore` | number | Quality score 0-100 (based on data completeness) |
| `leadQuality` | string | "hot" (70+), "warm" (40-69), or "cold" (<40) |
| `scrapedAt` | string | ISO timestamp of when the lead was scraped |

### Sample Output

```
{
  "businessName": "Austin Premier Plumbing",
  "address": "4521 Congress Ave, Austin, TX 78745",
  "phone": "+15125551234",
  "website": "https://austinpremierplumbing.com",
  "email": "info@austinpremierplumbing.com",
  "allEmails": [
    "info@austinpremierplumbing.com",
    "scheduling@austinpremierplumbing.com"
  ],
  "rating": 4.8,
  "reviewCount": 523,
  "category": "Plumber",
  "priceLevel": "$$",
  "hours": {
    "Monday": "7:00 AM - 6:00 PM",
    "Tuesday": "7:00 AM - 6:00 PM",
    "Wednesday": "7:00 AM - 6:00 PM",
    "Thursday": "7:00 AM - 6:00 PM",
    "Friday": "7:00 AM - 6:00 PM",
    "Saturday": "8:00 AM - 2:00 PM",
    "Sunday": "Closed"
  },
  "latitude": 30.2245,
  "longitude": -97.7633,
  "placeId": "ChIJ2dGMjMMRW4YRxTlQNfczEfw",
  "photos": [
    "https://lh5.googleusercontent.com/p/AF1QipN..."
  ],
  "isVerified": true,
  "googleMapsUrl": "https://www.google.com/maps/place/...",
  "emailSources": ["mailto", "contact-page"],
  "socialLinks": {
    "facebook": "https://facebook.com/austinpremierplumbing",
    "instagram": "https://instagram.com/austinpremierplumbing",
    "linkedin": null,
    "twitter": null,
    "youtube": null,
    "tiktok": null
  },
  "leadScore": 85,
  "leadQuality": "hot",
  "scrapedAt": "2026-03-02T14:30:00.000Z"
}
```

## Pricing

**Pay-per-event**: $0.008 per business lead with contact info. You only pay for leads that are successfully scraped and enriched.

| Leads | Cost |
| --- | --- |
| 50 | $0.40 |
| 100 | $0.80 |
| 250 | $2.00 |
| 500 | $4.00 |
| 1,000 | $8.00 |
| 5,000 | $40.00 |

## Tips for Best Results

1. **Be specific with your query** — "Italian restaurants in downtown Miami FL" returns better leads than just "restaurants"
2. **Use residential proxies** — Google blocks datacenter IPs aggressively. Apify residential proxies are strongly recommended.
3. **Start with a small test** — Run 50 leads first to verify data quality for your niche before scaling up
4. **Enable email enrichment** — The email data alone makes this 10x more valuable than basic scrapers
5. **Try different query variations** — "plumber in Austin" vs "plumbing services Austin TX" may return different results
6. **Export to CRM** — Download as CSV and import into HubSpot, Salesforce, Apollo, or Instantly.ai
7. **Filter by rating** — High-rated businesses (4.0+) are more likely to have active websites with contact info

## How It Works

### Phase 1 - Google Maps Search

The actor searches Google Maps using your query and automatically paginates through all available results. For each listing, it extracts the business name, address, phone number, rating, review count, category, price level, operating hours, GPS coordinates, photos, and Google Place ID.

### Phase 2 - Website Email Enrichment

For each business that has a website URL, the actor visits the site and applies multiple email extraction strategies:

- **Mailto link extraction** — Finds all `mailto:` links in the page HTML
- **Regex pattern scanning** — Scans page content for email-like patterns
- **Contact page crawling** — Follows links to /contact, /about, /team pages for additional emails
- **Meta tag parsing** — Checks meta tags and structured data for contact information
- **Social link extraction** — Finds LinkedIn, Facebook, Twitter/X, Instagram, YouTube, and TikTok profiles

### Phase 3 - Validation & Output

All extracted data is validated, deduplicated, and cleaned:

- Filters out generic emails (noreply@, no-reply@, admin@, webmaster@, etc.)
- Validates email format with regex
- Removes duplicate entries
- Normalizes phone number formats
- Outputs clean, structured JSON ready for export

## Integrations

Export your leads to:

- **CSV / Excel** — Download directly from the Apify console
- **Google Sheets** — Use Apify's built-in Google Sheets integration
- **Webhooks** — Send leads to your CRM or automation tool in real-time
- **Apify API** — Fetch results programmatically for custom integrations
- **Zapier / Make** — Connect to 5,000+ apps via automation platforms

## FAQ

**Q: How many leads can I scrape per run?**
A: Up to 5,000 leads per run. For larger datasets, run the actor multiple times with different search queries or locations.

**Q: How accurate are the emails?**
A: Emails are extracted directly from business websites, so accuracy is typically 80-90%. Generic/junk emails are automatically filtered out. Only emails found on the actual business domain are included.

**Q: Does this work for any country?**
A: Yes. Google Maps is available worldwide. Set the `language` parameter to match your target market (en, es, fr, de, pt, it, ja, zh, ko, ar).

**Q: How long does a run take?**
A: Approximately 3-8 minutes per 100 leads, depending on whether email enrichment is enabled and proxy speed.

**Q: Why do some businesses not have emails?**
A: Not all businesses have websites, and not all websites display email addresses publicly. Typically 40-70% of leads will have at least one email, depending on the industry and region.

**Q: Can I scrape Google Maps without proxies?**
A: Small runs (under 20 results) may work without proxies, but Google blocks non-residential IPs quickly. Residential proxies are strongly recommended for reliable results.

---

Built by [Sovereign AI](https://github.com/ryudi84) -- autonomous AI infrastructure for lead generation at scale.