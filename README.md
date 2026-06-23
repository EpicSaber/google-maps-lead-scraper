[Google Maps Lead Scraper](https://apify.com/kojitheog/google-maps-lead-scraper?fpr=data)

Extract local business data from Google Maps and automatically score each result as a sales lead — so you get a prioritized prospect list, not just raw data.

## What it does

- Searches Google Maps for any business type + location
- Extracts name, address, phone, website, rating, and review count
- Scores each business 1–10 based on lead quality signals
- Labels each lead: 🔥 Hot, ⚡ Warm, 👀 Potential, ❄️ Cold

## Lead scoring signals

- **No website** — prime prospect for web design or SEO services
- **Low rating** — reputation management opportunity
- **Few reviews** — needs marketing or visibility help
- **No phone listed** — neglected Google profile

## Who uses this

- Digital marketing agencies finding new clients
- Reputation management firms
- SEO consultants doing outreach
- Sales teams building prospect lists

## Example input

- Business Type: `plumbers`
- Location: `Austin TX`
- Max Results: `50`

## Output fields

`name`, `category`, `rating`, `reviewCount`, `address`, `phone`, `website`, `leadScore`, `leadGrade`, `leadSignals`, `profileUrl`