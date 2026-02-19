# Competitor Data Update Instructions

## Current State
The Echoes of Idols dashboard now has a competitor research section showing:
- Top 5 Etsy competitors for Stray Kids 3D prints
- Bestseller badges
- Price points
- Links to listings
- Market snapshot

## To Update with Live Data

The "Etsy Stray Kids Market Watch" cron job already runs daily. To integrate that data into the dashboard:

### Option 1: Update HTML directly in the cron job
Modify the cron job to update the `echoes-dashboard.html` file's competitor section with fresh data.

### Option 2: JSON data file approach (recommended)
1. Have the cron job write competitor data to `competitor-data.json`
2. Add JavaScript to `echoes-dashboard.html` to fetch and render this JSON
3. Keeps the HTML clean and data separate

### Sample JSON structure:
```json
{
  "lastUpdated": "2026-02-11T13:12:00+11:00",
  "totalResults": 990,
  "competitors": [
    {
      "rank": 1,
      "name": "Fan Made STRAY KIDS 3D Printed Keychain-Stay Skzoo",
      "shop": "Dedicatedtokpop",
      "price": "AU$10.31",
      "badge": "Bestseller",
      "url": "https://www.etsy.com/listing/..."
    }
  ]
}
```

### Next Steps:
1. Modify the Etsy Market Watch cron job to save data as JSON
2. Add fetch() call in dashboard JavaScript to load competitor-data.json
3. Render dynamically on page load

## Current Placeholder Data
The dashboard currently shows hardcoded competitor data from the Feb 11 market scan.
Replace the placeholder Etsy listing URLs with actual URLs from the cron job output.

- 2026-02-18 22:13 : Daily sync ran. Thangs analytics scraped successfully (views 9.1K, likes 155, downloads 255, total plan purchases 47, unpaid earnings A$1,007.59). Cults3D `/en/sales` was login-gated; existing Cults metrics kept.
- 2026-02-19 02:02 : Daily sync ran. Thangs analytics scraped successfully (views 9.1K, likes 155, downloads 255, total plan purchases 47, unpaid earnings A$1,007.59). Cults3D `/en/sales` was login-gated; existing Cults metrics kept.
- 2026-02-20 02:01 : Daily sync ran. Thangs analytics scraped successfully (views 9.1K, likes 155, downloads 255, total plan purchases 47, unpaid earnings A$1,007.59). Cults3D `/en/sales` redirected to log-in; existing Cults metrics kept.
