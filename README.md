[Google Maps Lead Scraper](https://apify.com/vaunted/google-maps-lead-scraper?fpr=data)

A high-performance Google Maps lead scraper built for serious email extraction. Pull verified emails, phone numbers, and social media profiles from any business on Google Maps — at scale.

## Why This Actor?

Most Google Maps scrapers only check the homepage for a visible email link. That misses the vast majority of business emails. This actor was built from scratch to go deeper.

| Feature | What You Get |
| --- | --- |
| **Email hit rate** | **50–60%** of businesses — most actors return far fewer |
| **Speed** | Lightweight HTTP-only engine — no heavy browser overhead |
| **Email accuracy** | Built-in SMTP verification confirms every address is real |
| **Coverage** | Decodes hidden, obfuscated, and protected emails others miss |
| **Smart filtering** | Auto-removes placeholder, system, and false-positive emails |
| **Social profiles** | Facebook, Instagram, LinkedIn, Twitter/X, YouTube, TikTok, Pinterest |
| **Phone numbers** | From the Google listing + additional numbers found on websites |
| **Cost efficiency** | No browser rendering = significantly lower compute costs |

---

## How to Use

### Step 1: Enter your search

Tell it **what** you're looking for and **where**:

- **Search Queries** — Business types like `"dentist"`, `"plumber"`, `"real estate agent"`, `"restaurant"`
- **Locations** — Cities or areas like `"Miami, FL"`, `"London, UK"`, `"Sydney, Australia"`
- **Google Maps URLs** — Or paste Google Maps search URLs directly (e.g. `google.com/maps/search/restaurants/@40.7,-74.0,13z`)

Each query runs against every location. So 3 queries × 2 locations = 6 separate searches.

### Step 2: Narrow your area (optional)

Use the **Geolocation** fields to zero in on a specific region:

- **Country** — Select from 60+ countries for precise targeting
- **State / Province** — e.g. `"California"`, `"Ontario"`
- **City** — e.g. `"Miami"` (don't repeat the state/country here)
- **Postal / ZIP Code** — Target a single postal code area

These generate additional search combinations automatically. For example, searching "dentist" with location "Miami, FL" and country "US" + state "Florida" will run two searches: one for "dentist in Miami, FL" and one for "dentist in Florida, US".

### Step 3: Configure filters (or just use the defaults)

The defaults work great out of the box. But you can tweak:

- **Max Results Per Search** — How many businesses per search (up to 500)
- **Only Output Businesses With Emails** — Skip businesses where no email was found (great for lead gen)
- **Website Availability Filter** — Only scrape places with (or without) a website listed
- **Category Filter** — Only include specific Google Maps categories (e.g. `"restaurant"` matches `"Italian restaurant"`, `"Chinese restaurant"`, etc.)
- **Minimum Star Rating** — Filter out low-rated businesses
- **Skip Permanently Closed Places** — Automatically exclude closed listings
- **Verify Emails (SMTP)** — Confirm emails actually exist before including them (recommended)
- **Deep Email Search** — Look beyond the homepage for emails (recommended — most emails are on contact pages)

### Step 4: Run & export

Hit **Start** and wait. Results appear in the dataset as they're found. Export to:

- **CSV** or **Excel** — Perfect for cold outreach
- **JSON** — For CRM import or automation pipelines
- **Google Sheets** — Direct integration

---

## Example Input

```
{
    "searchQueries": ["dentist", "orthodontist"],
    "locations": ["Los Angeles, CA", "San Francisco, CA"],
    "country": "us",
    "state": "California",
    "maxResultsPerSearch": 200,
    "onlyWithEmails": true,
    "onlyWithWebsite": "withWebsite",
    "emailVerification": true,
    "deepSearch": true
}
```

This will search for dentists and orthodontists across LA, SF, and California (US) — only returning businesses that have a website and verified emails.

---

## What You Get (Output)

Every result includes:

| Field | Example |
| --- | --- |
| **Business Name** | Smile Dental Care |
| **Category** | Dentist |
| **Emails** | [info@smiledental.com](mailto:info@smiledental.com), [appointments@smiledental.com](mailto:appointments@smiledental.com) |
| **Phone** | +1 (310) 555-0123 |
| **Website** | [https://www.smiledental.com](https://www.smiledental.com) |
| **Address** | 123 Main St, Los Angeles, CA 90001 |
| **Rating** | 4.8 |
| **Reviews** | 245 |
| **Facebook** | [https://facebook.com/smiledental](https://facebook.com/smiledental) |
| **Instagram** | [https://instagram.com/smiledental](https://instagram.com/smiledental) |
| **LinkedIn** | [https://linkedin.com/company/smiledental](https://linkedin.com/company/smiledental) |
| **Twitter / X** | [https://x.com/smiledental](https://x.com/smiledental) |
| **YouTube** | [https://youtube.com/@smiledental](https://youtube.com/@smiledental) |
| **TikTok** | [https://tiktok.com/@smiledental](https://tiktok.com/@smiledental) |
| **Website Phones** | Additional phone numbers found on the website |
| **Coordinates** | Latitude / Longitude |
| **Opening Hours** | Monday–Friday: 8 AM – 5 PM |
| **Google Maps URL** | Direct link to the listing |
| **Place ID** | Google's unique business identifier |

---

## Tips for Best Results

### Get more emails

- **Keep "Deep Email Search" enabled** — Many businesses only list their email on the contact page, not the homepage. This is the single biggest factor for email hit rate.
- **Enable "Verify Emails (SMTP)"** — Adds a few seconds per email but ensures you only get real, deliverable addresses.
- **Use "Website Availability Filter → Only with website"** — Businesses without websites can't have emails extracted. Skip them to save time.

### Save money

- **Use "Only Output Businesses With Emails"** — If you're doing outreach, you don't need businesses without emails. This keeps your dataset clean and focused.
- **Be specific with locations** — `"plumber in Brooklyn, NY"` works better than `"plumber in New York"`. Specific searches = fewer wasted results.

### Scale up

- **Use multiple specific searches** instead of one broad one — Google Maps caps at ~500 results per search. Break large areas into neighborhoods or zip codes.
- **Use the geolocation fields** — Setting Country + State generates additional search combinations automatically, covering more ground per run.
- **Use residential proxies** — Already configured by default. Google Maps is strict about blocking, and residential proxies keep your runs stable.

---

## Advanced Settings

These are under the "Advanced" section in the input UI:

| Setting | Default | What it does |
| --- | --- | --- |
| **Max Pages Per Website** | 5 | How many subpages to scan per website. Higher = more thorough, slightly slower. |
| **Results Language** | English | The language Google Maps results appear in. Doesn't affect email extraction. |

---

## Use Cases

- **Lead Generation** — Build targeted B2B email lists by industry and location
- **Local SEO Agencies** — Audit potential clients and their online presence
- **Sales Prospecting** — Find decision-maker contact info for local businesses
- **Market Research** — Map competitors in a geographic area
- **Recruitment** — Find businesses in specific industries to reach out to
- **Real Estate** — Contact property managers, agents, and related businesses

---

## FAQ

**Q: Why don't some businesses have emails?**
Not every business publishes an email on their website. Some only use contact forms, phone numbers, or social media messaging. A 50–60% email hit rate means we're finding every available email — the rest genuinely don't have one.

**Q: Are the emails verified?**
Yes, when "Verify Emails (SMTP)" is enabled (it is by default). We check with the actual mail server to confirm the email address exists and can receive messages.

**Q: Can I search outside the US?**
Absolutely. Enter any city or country in the Locations field, or use the Country dropdown to select from 60+ countries. Works worldwide — `"restaurant in Tokyo, Japan"`, `"plumber in London, UK"`, etc.

**Q: Can I paste a Google Maps URL instead of typing a query?**
Yes. Use the "Google Maps URLs" field to paste any Google Maps search or place URL. The actor will parse the query and coordinates automatically.

**Q: How is this different from a basic Google Maps scraper?**
A basic approach only checks the homepage for a visible email link. This actor scans multiple subpages per website, decodes obfuscated and protected emails, and verifies every address via SMTP — resulting in significantly more verified contacts per run.

**Q: Will this get my IP blocked?**
No. The actor uses Apify's residential proxy network by default. Your IP is never exposed.

**Q: Can I integrate this with my CRM?**
Yes. Export results as JSON or CSV and import into any CRM (HubSpot, Salesforce, Pipedrive, etc.). You can also use Apify integrations to pipe results directly into Google Sheets, Zapier, Make, or webhooks.

---

## Support

Having issues or need a custom feature? Reach out via the Apify platform — we respond within 24 hours.