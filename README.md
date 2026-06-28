[Immobiliare It Scraper](https://apify.com/shahidirfan/immobiliare-it-scraper?fpr=data)

# Immobiliare.it Listings Scraper

Extract Immobiliare.it property listings with structured details in a single run. Collect prices, property specs, location data, agency information, and image links for market research, lead generation, pricing intelligence, and portfolio monitoring.

## Features

- **Search URL input** — Start from any valid Immobiliare.it search page and collect matching listings.
- **Paginated collection** — Gather results across multiple pages until your limit is reached.
- **Rich property records** — Capture pricing, rooms, bathrooms, surface, floor, location, and agency details.
- **Image-rich output** — Collect the primary image plus all available image variants for each listing.
- **Clean datasets** — Empty values are removed so output records stay compact and easy to process.
- **Deduplicated results** — Avoid duplicate listings during multi-page collection.

## Use Cases

### Market Research

Track inventory, asking prices, and property characteristics across neighborhoods, cities, or regions. Build dependable datasets for repeat analysis and reporting.

### Pricing Intelligence

Compare listing prices across property types and locations. Monitor changes over time to support valuation, buying, and selling decisions.

### Lead Generation

Collect agency names, phone numbers, and listing details for outbound prospecting. Build lead lists for brokerage, referral, and partnership workflows.

### Portfolio Monitoring

Watch specific markets for new opportunities, luxury listings, or high-value properties. Keep a recurring watchlist without manual browsing.

### Data Operations

Export structured property data to spreadsheets, BI tools, databases, and automation workflows. Keep your downstream systems updated with fresh listings.

---

## Input Parameters

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `startUrl` | String | No | `"https://www.immobiliare.it/en/vendita-case/agrigento/"` | Immobiliare.it search URL to scrape. |
| `results_wanted` | Integer | No | `20` | Maximum number of listings to collect. |
| `max_pages` | Integer | No | `5` | Maximum number of result pages to process. |
| `proxyConfiguration` | Object | No | `{"useApifyProxy": false}` | Optional proxy settings for better reliability on larger runs. |

---

## Output Data

Each dataset item can contain the following fields:

| Field | Type | Description |
| --- | --- | --- |
| `listing_id` | Integer | Unique listing ID. |
| `listing_uuid` | String | Unique listing UUID. |
| `title` | String | Listing title. |
| `url` | String | Listing detail page URL. |
| `anchor` | String | Listing anchor text. |
| `contract` | String | Listing contract type. |
| `property_type` | String | Property type name. |
| `property_type_id` | Integer/String | Property type identifier. |
| `category` | String | Property category name. |
| `category_id` | Integer/String | Property category identifier. |
| `price` | String | Formatted asking price. |
| `price_value` | Number | Numeric price value when available. |
| `surface` | String | Surface area text. |
| `rooms` | String | Number of rooms. |
| `bedrooms` | String | Number of bedrooms. |
| `bathrooms` | String | Number of bathrooms. |
| `floor` | String | Floor label. |
| `floor_number` | String | Numeric floor value when available. |
| `condition` | String | Property condition. |
| `heating` | String | Heating label. |
| `features` | Array | Raw feature metadata. |
| `feature_labels` | Array | Human-readable feature labels. |
| `address` | String | Street or address snippet. |
| `city` | String | City name. |
| `macrozone` | String | Local area or neighborhood label. |
| `province` | String | Province name. |
| `region` | String | Region name. |
| `country` | String | Country name. |
| `country_id` | String | Country identifier. |
| `latitude` | Number | Latitude coordinate. |
| `longitude` | Number | Longitude coordinate. |
| `agency_id` | Integer/String | Agency identifier. |
| `agency_name` | String | Agency display name. |
| `agency_url` | String | Agency profile URL. |
| `agency_phones` | Array | Agency contact numbers. |
| `agent_name` | String | Agent or supervisor name. |
| `image_url_small` | String | Primary small image URL. |
| `image_url_medium` | String | Primary medium image URL. |
| `image_url_large` | String | Primary large image URL. |
| `images_count` | Integer | Number of images available. |
| `image_urls_small` | Array | Small image URLs for the listing. |
| `image_urls_medium` | Array | Medium image URLs for the listing. |
| `image_urls_large` | Array | Large image URLs for the listing. |
| `images` | Array | Flattened image URLs using the best available size. |
| `is_new` | Boolean | Indicates a newly listed property. |
| `is_luxury` | Boolean | Indicates a luxury property. |
| `page` | Integer | Search result page number. |
| `position_on_page` | Integer | Position of the listing on the page. |
| `source_search_url` | String | Search URL used for the run. |
| `scraped_at` | String | ISO timestamp of extraction. |

---

## Usage Examples

### Basic Extraction

Collect a small batch for quick testing.

```
{
  "startUrl": "https://www.immobiliare.it/en/vendita-case/agrigento/",
  "results_wanted": 20
}
```

### Larger Collection

Collect more results across additional pages.

```
{
  "startUrl": "https://www.immobiliare.it/en/vendita-case/agrigento/",
  "results_wanted": 200,
  "max_pages": 20
}
```

### Proxy Enabled Run

Use proxies for more reliable large-scale collection.

```
{
  "startUrl": "https://www.immobiliare.it/en/vendita-case/agrigento/",
  "results_wanted": 100,
  "max_pages": 10,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  }
}
```

---

## Sample Output

```
{
  "listing_id": 124223331,
  "listing_uuid": "c9bd2859-5eda-5b4b-a3bf-023ddbd6776c",
  "title": "3-room flat via San Michele 28, Centro Storico, Agrigento",
  "url": "https://www.immobiliare.it/en/annunci/124223331/",
  "anchor": "3-room flat via San Michele 28, Centro Storico, Agrigento",
  "contract": "sale",
  "property_type": "Apartment",
  "property_type_id": 1,
  "category": "Residential",
  "category_id": 1,
  "price": "€ 21,000",
  "price_value": 21000,
  "surface": "70 m²",
  "rooms": "3",
  "bedrooms": "2",
  "bathrooms": "2",
  "floor": "1°",
  "floor_number": "1",
  "condition": "Good condition",
  "heating": "Independent",
  "address": "Via San Michele 28",
  "city": "Agrigento",
  "province": "Agrigento",
  "region": "Sicilia",
  "country": "Italy",
  "latitude": 37.311,
  "longitude": 13.576,
  "agency_name": "Affiliato Tecnocasa: AGRIGENTO MEDIAZIONI D.I.",
  "images_count": 10,
  "image_url_medium": "https://pwm.im-cdn.it/image/1807380501/m-c.jpg",
  "image_urls_large": [
    "https://pwm.im-cdn.it/image/1807380501/xxl.jpg",
    "https://pwm.im-cdn.it/image/1807381115/xxl.jpg"
  ],
  "page": 1,
  "position_on_page": 1,
  "source_search_url": "https://www.immobiliare.it/en/vendita-case/agrigento/",
  "scraped_at": "2026-03-18T08:12:00.000Z"
}
```

---

## Tips for Best Results

### Use Working Search URLs

- Start with a valid Immobiliare.it search page.
- Verify the URL in a browser before running large jobs.

### Tune Collection Limits

- Use `results_wanted: 20` for quick validation runs.
- Increase `max_pages` only when you need broader coverage.

### Improve Reliability

- Enable proxy settings for larger or repeated runs.
- Prefer smaller recurring runs over one very large scrape.

### Keep Inputs Focused

- Use one market or area per run for cleaner datasets.
- Collect consistent runs if you plan to compare trends over time.

---

## Integrations

Connect the dataset output with:

- **Google Sheets** — Build live property trackers.
- **Airtable** — Maintain searchable listing databases.
- **Looker Studio / Power BI** — Create pricing and inventory dashboards.
- **Webhooks** — Send fresh listing data to your backend.
- **Make** — Trigger end-to-end real estate automations.
- **Zapier** — Forward new records to CRM and alerts.

### Export Formats

- **JSON** — Best for APIs and applications.
- **CSV** — Ideal for spreadsheets and reporting.
- **Excel** — Useful for business analysis and sharing.
- **XML** — Fits structured integrations.

---

## Frequently Asked Questions

### How many listings can I collect per run?

You can collect as many listings as are available in the search results, limited by `results_wanted` and `max_pages`.

### Can I use this for rentals and sales?

Yes. Use a valid Immobiliare.it search URL for the market you want to collect.

### Does it return agency contact details?

Yes. The output can include agency names, profile URLs, and contact numbers when available.

### Are images included?

Yes. The output includes the primary image plus image arrays for different sizes.

### Why are some fields missing in certain records?

Some listings do not publish every attribute. Empty values are removed from output items to keep them clean.

### Can I run this on a specific city or neighborhood?

Yes. Point `startUrl` to the Immobiliare.it search page for that area.

---

## Support

For issues or feature requests, contact support through the Apify Console.

### Resources

- [Apify Documentation](https://docs.apify.com/)
- [Apify API Reference](https://docs.apify.com/api/v2)
- [Scheduling Runs](https://docs.apify.com/schedules)

---

## Legal Notice

This actor is designed for legitimate data collection purposes. Users are responsible for ensuring compliance with applicable laws and website terms of service. Use collected data responsibly and respect rate limits.