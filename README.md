[Google Maps Lead Scraper](https://apify.com/abdullah_maven/google-maps-lead-scraper?fpr=data)

The most complete Google Maps scraper on Apify. Extract business leads with **built-in email and social media enrichment** -- all in one actor. No need to chain multiple scrapers together.

Search any business type in any location worldwide. Get names, addresses, phone numbers, websites, **email addresses**, and **social media links** (Facebook, Instagram, Twitter/X, LinkedIn, YouTube, TikTok) for every business.

## Why use this over other Google Maps scrapers?

| Feature | Other Scrapers | This Actor |
| --- | --- | --- |
| Business data from Google Maps | Yes | Yes |
| Email extraction from websites | Requires separate actor | **Built-in** |
| Social media links | Not included | **All 6 platforms** |
| Additional phone numbers | Not included | **Included** |
| Price per 1,000 leads | $2-5 (Maps only) | **$2 (everything included)** |

## Who is this for?

- **Marketing agencies** building prospect lists for outreach campaigns
- **Sales teams** finding decision-maker contacts by industry and location
- **SEO agencies** identifying local businesses for link building and pitching
- **Recruiters** discovering growing companies in target markets
- **Market researchers** analyzing business density, competition, and ratings

## Output data per lead

Each extracted business includes:

| Field | Source | Description |
| --- | --- | --- |
| `name` | Google Maps | Business name |
| `category` | Google Maps | Business type (e.g., "Restaurant", "Dentist") |
| `address` | Google Maps | Full street address |
| `phone` | Google Maps | Primary phone number |
| `website` | Google Maps | Business website URL |
| `rating` | Google Maps | Star rating (0-5) |
| `reviewCount` | Google Maps | Number of Google reviews |
| `priceLevel` | Google Maps | Price indicator ($, $$, $$$) |
| `latitude` / `longitude` | Google Maps | GPS coordinates |
| `googleMapsUrl` | Google Maps | Direct link to listing |
| `emails` | Website | Email addresses found on business website |
| `socialLinks.facebook` | Website | Facebook page URL |
| `socialLinks.instagram` | Website | Instagram profile URL |
| `socialLinks.twitter` | Website | Twitter/X profile URL |
| `socialLinks.linkedin` | Website | LinkedIn company URL |
| `socialLinks.youtube` | Website | YouTube channel URL |
| `socialLinks.tiktok` | Website | TikTok profile URL |
| `extraPhones` | Website | Additional phone numbers |
| `openingHours` | Google Maps | Business hours |
| `searchQuery` | - | The search query that found this business |

## Example output

```
[
    {
        "name": "Corner Restaurant",
        "category": "Restaurant",
        "address": "110 E 2nd St, Austin, TX 78701",
        "phone": "(512) 608-4488",
        "website": "https://www.cornerrestaurantaustin.com",
        "rating": 4.8,
        "reviewCount": 1243,
        "priceLevel": "$$",
        "latitude": 30.2654,
        "longitude": -97.7430,
        "googleMapsUrl": "https://www.google.com/maps/place/Corner+Restaurant/...",
        "emails": ["socialmedia@cornerrestaurantaustin.com"],
        "socialLinks": {
            "facebook": "https://facebook.com/cornerrestaurantaustin",
            "instagram": "https://instagram.com/cornerrestaurantaustin",
            "twitter": null,
            "linkedin": null,
            "youtube": null,
            "tiktok": null
        },
        "extraPhones": [],
        "openingHours": "Open 24 hours",
        "searchQuery": "restaurants in Austin, TX",
        "enrichedAt": "2026-04-01T20:35:37.000Z"
    },
    {
        "name": "Odd Duck",
        "category": "Restaurant",
        "address": "1201 S Lamar Blvd, Austin, TX 78704",
        "phone": "(512) 433-6521",
        "website": "https://www.oddduckaustin.com",
        "rating": 4.7,
        "reviewCount": 3891,
        "priceLevel": "$$$",
        "latitude": 30.2520,
        "longitude": -97.7640,
        "googleMapsUrl": "https://www.google.com/maps/place/Odd+Duck/...",
        "emails": ["info@oddduckaustin.com", "events@oddduckaustin.com"],
        "socialLinks": {
            "facebook": "https://facebook.com/oddduckaustin",
            "instagram": "https://instagram.com/oddduckaustin",
            "twitter": "https://twitter.com/oddduckaustin",
            "linkedin": null,
            "youtube": null,
            "tiktok": null
        },
        "extraPhones": ["(512) 433-6520"],
        "openingHours": "11 AM - 10 PM",
        "searchQuery": "restaurants in Austin, TX",
        "enrichedAt": "2026-04-01T20:35:37.000Z"
    }
]
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQueries` | string[] | *required* | Google Maps search queries (e.g., `["dentists in Chicago, IL"]`) |
| `maxResultsPerQuery` | number | 100 | Max results per query (up to 500) |
| `language` | string | "en" | Language for Google Maps (15 languages supported) |
| `includeEmails` | boolean | true | Extract emails from business websites |
| `includeSocials` | boolean | true | Extract social media links |
| `includeExtraPhones` | boolean | true | Extract additional phone numbers |
| `enrichmentDepth` | string | "deep" | "homepage" (fast) or "deep" (checks /contact, /about pages too) |
| `minRating` | number | 0 | Minimum star rating filter (0-5) |
| `minReviews` | number | 0 | Minimum review count filter |
| `maxConcurrency` | number | 5 | Parallel processing (1-20) |
| `proxyConfig` | object | - | Proxy settings (residential recommended) |

## How it works

**Phase 1 -- Google Maps (Playwright)**: Searches Google Maps for your query, scrolls through results, collects all business URLs, then visits each one to extract the full business profile (name, address, phone, website, rating, reviews, hours, coordinates).

**Phase 2 -- Website Enrichment (Cheerio)**: For each business with a website, makes fast HTTP requests to the homepage and contact/about pages. Extracts email addresses (mailto links + regex patterns + obfuscated emails), social media profile URLs for all 6 major platforms, and additional phone numbers.

**Phase 3 -- Assembly**: Merges all data, deduplicates emails and phone numbers, filters out generic/noreply addresses, applies your rating/review filters, and outputs clean enriched leads.

## Tips for best results

- **Include location in your query**: "plumbers in Austin, TX" works better than just "plumbers"
- **Use residential proxies**: Google Maps blocks datacenter IPs more aggressively
- **Deep enrichment** (default): Crawls /contact and /about pages for 30-50% more emails
- **Start small**: Test with `maxResultsPerQuery: 10` to verify your queries before scaling up
- **Multiple queries**: Run several queries in one batch for better efficiency

## Supported countries

Works globally -- any location Google Maps covers. Tested across US, UK, Canada, Germany, Japan, Brazil, and more. Supports 15 languages for localized results.

## Pricing

**Pay Per Event**: $0.002 per lead (~$2 per 1,000 leads).

This includes both the Google Maps extraction AND the website email/social enrichment. No hidden costs. Platform usage is included.

## Technical details

- Built with [Crawlee](https://crawlee.dev/) + TypeScript
- Uses Playwright for Google Maps (JavaScript rendering)
- Uses CheerioCrawler for website enrichment (10-50x faster than browser-based crawling)
- Automatic retry and error handling for unreliable business websites
- Smart email filtering removes noreply/automated/generic addresses
- Deduplication across all results
- Fingerprint randomization for anti-detection