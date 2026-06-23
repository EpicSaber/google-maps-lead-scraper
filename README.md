[Google Maps Lead Scraper](https://apify.com/aleksandar77/google-maps-lead-scraper?fpr=data)

Extract leads from Google Maps — names, addresses, phone numbers, emails, ratings, reviews, opening hours, coordinates, and social media links. Everything included in one simple price.

**Pricing: $3.00 per 1,000 places** — emails, reviews, and social media links included at no extra cost.

---

## 📍 What is Google Maps Lead Scraper?

Google Maps Lead Scraper helps you collect structured business data from Google Maps at scale, so you can focus on what matters — closing deals, analyzing markets, and growing your business.

- **Generate qualified leads** — extract business names, emails, phone numbers, and websites to build ready-to-use prospect lists
- **Analyze any market** — compare ratings, review counts, and categories across regions to spot gaps and opportunities
- **Track competitors** — monitor where competitors operate, how customers rate them, and how their presence changes over time
- **Enrich your CRM** — add missing phone numbers, emails, social profiles, and coordinates to your existing contact database
- **Automate research** — replace hours of manual Google Maps browsing with a single API call that delivers clean, structured data

### Why choose this scraper?

|  | This Scraper | Other scrapers |
| --- | --- | --- |
| 💰 **Price per 1,000 places** | **$3.00** | $2.10 + add-ons = **$4.00+** |
| 📧 **Email extraction** | ✅ Included | 💰 Paid add-on |
| 📱 **Social media links** | ✅ Included | 💰 Paid add-on |
| ⭐ **Minimum rating filter** | ✅ Built-in | ❌ Not available |
| 🔄 **Deduplication** | ✅ Automatic | ❌ Not available |
| 📝 **Reviews** | ✅ Included | 💰 Paid add-on |
| 💰 **Real cost with all features** | **$3.00** | **$4.00+** |

Other scrapers look cheaper at first glance, but the add-ons add up fast. With us, what you see is what you pay — no surprises.

---

## 📊 What data does it extract?

|  |  |
| --- | --- |
| 🏪 Business name & category | 📍 Full address & coordinates (lat/lng) |
| ☎️ Phone number | 🌐 Website URL |
| 📧 Email address (from business website) | ⭐ Rating & total review count |
| 🕐 Full weekly opening hours | 💲 Price level |
| 📸 Cover image URL | 🆔 Google Place ID & Maps URL |
| 📱 Social media links (Facebook, Instagram, Twitter/X, LinkedIn, YouTube, TikTok) | 🔒 Permanently/temporarily closed status |
| 💬 Individual reviews (author, stars, text, date) | 🕒 Scrape timestamp |

Email addresses are extracted directly from each business's website — no extra cost, no add-on required.

---

## ⬇️ Input

You can configure the scraper using the Apify Console UI or programmatically via the API.

### Search mode

Enter a **search term** and an optional **location** to find businesses, just like you would on Google Maps.

**Good search terms** — distinct keywords that cover different business types:

> `restaurant`, `bar`, `pharmacy`, `gym`, `dentist`

**Avoid overlapping terms** — these produce duplicate results and waste time:

> `restaurant`, `restaurants`, `italian restaurant`, `dining`

### Direct URLs mode

Already have Google Maps place URLs? Paste them directly and skip the search step entirely. Useful when you need to refresh data for a known set of businesses.

### Input fields

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQuery` | string | — | Search term, e.g. "restaurant", "dentist". Required unless using `directUrls`. |
| `location` | string | — | Location context, e.g. "Berlin, Germany", "Manhattan, NY". Optional. |
| `directUrls` | array | `[]` | List of Google Maps place URLs to scrape directly (bypasses search). |
| `maxPlaces` | integer | `20` | Maximum number of places to scrape (1–500). |
| `minRating` | number | — | Only return places with this rating or higher (e.g. `4.0`). |
| `scrapeEmails` | boolean | `true` | Visit each business website and extract contact email addresses. |
| `scrapeReviews` | boolean | `false` | Extract individual reviews for each place (slower). |
| `maxReviews` | integer | `10` | Maximum reviews to collect per place when reviews are enabled (1–100). |
| `exportFormat` | string | `"json"` | Output format: `"json"`, `"csv"`, or `"both"`. |
| `language` | string | `"en"` | Language code for Google Maps results (e.g. `"en"`, `"de"`, `"fr"`, `"es"`). |

### Input example

```
{
    "searchQuery": "coffee shop",
    "location": "Amsterdam, Netherlands",
    "maxPlaces": 50,
    "minRating": 4.0,
    "scrapeEmails": true,
    "scrapeReviews": true,
    "maxReviews": 5,
    "exportFormat": "json",
    "language": "en"
}
```

---

## ⬆️ Output

Results are stored in an Apify Dataset. You can view them as a table, download as JSON, CSV, or Excel, or access them via the API.

### Table view

The dataset table shows a clean overview of all scraped places with columns for name, category, address, phone, email, website, rating, review count, opening hours, coordinates, and price level. You can sort and filter directly in the Apify Console.

### JSON output

Here is an example of the data you get for a single scraped place:

```
{
    "name": "The Coffee House",
    "category": "Coffee shop",
    "place_id": "ChIJN1t_tDeuEmsRUsoyG83frY4",
    "google_maps_url": "https://www.google.com/maps/place/The+Coffee+House/data=...",
    "address": "Prinsengracht 124, 1015 EA Amsterdam",
    "city": "",
    "latitude": 52.3738,
    "longitude": 4.8842,
    "phone": "+31 20 555 0123",
    "website": "https://thecoffeehouse.nl",
    "email": "hello@thecoffeehouse.nl",
    "rating": 4.6,
    "reviews_count": 843,
    "price_level": "Moderate",
    "permanently_closed": false,
    "temporarily_closed": false,
    "opening_hours": [
        "Monday: 7:00 AM – 8:00 PM",
        "Tuesday: 7:00 AM – 8:00 PM",
        "Wednesday: 7:00 AM – 8:00 PM",
        "Thursday: 7:00 AM – 9:00 PM",
        "Friday: 7:00 AM – 9:00 PM",
        "Saturday: 8:00 AM – 9:00 PM",
        "Sunday: 8:00 AM – 6:00 PM"
    ],
    "social_media": {
        "instagram": "https://instagram.com/thecoffeehouse.nl",
        "facebook": "https://facebook.com/TheCoffeeHouseAMS"
    },
    "image_url": "https://lh5.googleusercontent.com/p/AF1Qip...",
    "reviews": [
        {
            "author": "Maria S.",
            "stars": 5,
            "text": "Best flat white in Amsterdam! Cozy atmosphere and friendly staff.",
            "date": "2 weeks ago"
        },
        {
            "author": "Thomas K.",
            "stars": 4,
            "text": "Great coffee, a bit crowded on weekends.",
            "date": "1 month ago"
        }
    ],
    "scraped_at": "2026-04-08T14:30:22"
}
```

### CSV & Excel export

CSV and Excel exports automatically flatten nested fields for easy use in spreadsheets:

- **Opening hours** → semicolon-separated string
- **Social media** → JSON string
- **Reviews** → JSON string (up to 5 per place)

You can download exports directly from the Apify Console or request them via the API.

---

## 💡 Tips for best results

### Getting more places

- Use **distinct search terms** rather than variations of the same word
- Add a **location** to focus results on a specific area
- Increase `maxPlaces` up to 500 per run

### Improving data quality

- Enable **email scraping** (`scrapeEmails: true`) to get direct contact emails — this adds ~1–2 seconds per place but significantly enriches your data
- Use **minimum rating filter** (`minRating: 4.0`) to focus on high-quality businesses only
- Enable **reviews** for sentiment analysis or to understand customer feedback

### Saving on costs

- Disable `scrapeEmails` if you don't need emails — runs will be faster and cheaper
- Disable `scrapeReviews` unless you specifically need review text — this is the slowest feature
- Use `directUrls` to scrape only the places you care about instead of running broad searches

---

## 🔌 API access

You can run this scraper programmatically using the Apify API. Start runs, retrieve datasets, and integrate with your existing tools.

### Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run_input = {
    "searchQuery": "restaurant",
    "location": "Berlin, Germany",
    "maxPlaces": 100,
    "scrapeEmails": True,
}

run = client.actor("YOUR_ACTOR_ID").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item["name"], item["email"], item["phone"])
```

### Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('YOUR_ACTOR_ID').call({
    searchQuery: 'restaurant',
    location: 'Berlin, Germany',
    maxPlaces: 100,
    scrapeEmails: true,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => console.log(item.name, item.email, item.phone));
```

You can also use **webhooks** to trigger actions when a run completes — send data to Google Sheets, Slack, your CRM, or any webhook-compatible service.

---

## ❓ FAQ

### How does this scraper work?

It works exactly like a person searching Google Maps manually — but faster. The scraper opens Google Maps, enters your search query, scrolls through results, then visits each place page to extract all available information. Email addresses are collected by visiting the business's own website and scanning for contact information.

### How is email scraping included in the base price?

Most scrapers charge extra for email extraction because it requires visiting each business's website separately. We include it at no extra cost because we believe contact data is essential for lead generation — and you shouldn't have to pay twice for it.

### Can I scrape places from multiple locations?

Yes. You can run separate searches for different locations, or use the batch mode to automatically combine multiple search terms with multiple locations and deduplicate the results.

### Can I scrape Google Maps reviews?

Yes. Set `scrapeReviews` to `true` and the scraper will collect individual reviews for each place, including the author name, star rating, review text, and date. You can control how many reviews per place with `maxReviews`.

### What if a place doesn't have an email or phone number?

The scraper returns all available data. If a field isn't present on Google Maps or the business website, it will be returned as an empty string. You'll never be charged for a place that fails to scrape entirely.

### How fast is it?

Speed depends on your settings. With email scraping enabled, expect roughly 8–15 seconds per place. Without emails, it's faster at 3–6 seconds per place. Reviews add additional time depending on `maxReviews`.

### Can I filter by rating?

Yes. Use the `minRating` field (e.g. `4.0`) and the scraper will automatically skip places below that threshold. You won't be charged for filtered-out places.

### What formats can I export?

JSON, CSV, and Excel (.xlsx). You can download any format from the Apify Console, or set `exportFormat` in the input to automatically generate a CSV in the Key-Value Store.

### Can I integrate this with other tools?

Yes. Through the Apify platform you can connect this scraper with Google Sheets, Slack, Make (Integromat), Zapier, and many other services using webhooks or direct API integration.

### Is it legal to scrape Google Maps?

Web scraping of publicly available data is generally legal. However, you are responsible for complying with Google's Terms of Service, GDPR, CCPA, and any other applicable regulations in your jurisdiction. Do not use scraped data for purposes that violate privacy laws or Apify's Acceptable Use Policy.

---

## 📬 Feedback & support

Found a bug or have a feature request? Open an issue in the **Issues** tab on this Actor's page. We actively monitor feedback and ship fixes regularly.

---

## Legal notice

This Actor scrapes publicly available data from Google Maps.

You are responsible for ensuring your use case complies with:

- Google's [Terms of Service](https://policies.google.com/terms)
- Applicable data protection laws (GDPR, CCPA, etc.)
- Apify's [Acceptable Use Policy](https://docs.apify.com/legal)

Do not scrape personal data without a legitimate legal basis.