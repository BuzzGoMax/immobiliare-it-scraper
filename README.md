[Immobiliare It Scraper](https://apify.com/igolaizola/immobiliare-it-scraper?fpr=data)

## 🤖 What does Immobiliare.it Scraper do?

Immobiliare.it Scraper lets you seamlessly extract property listings from [Immobiliare.it](https://www.immobiliare.it) for personal analysis, market research, or lead generation.

Depending on your needs, the scraper can collect:

- 🏠 Properties for sale (`buy`)
- 🏡 Properties for rent (`rent`)
- 📉 Auction listings (`auction`)

## 💡 Why scrape Immobiliare.it?

[Immobiliare.it](https://www.immobiliare.it) is Italy’s leading property portal, featuring hundreds of thousands of listings nationwide. By scraping its data, you can:

- 📈 Track price movements and market trends in specific provinces or municipalities
- 🔍 Monitor new listings, auctions, and rental opportunities for real-time insights
- 🎯 Generate high-quality leads for agents, investors, and developers
- 🗺️ Analyze geographic distribution, amenities, and proximity to services around listings

## 🚀 How to use Immobiliare.it Scraper

1. **Add the actor** – Sign in to Apify and add **Immobiliare.it Scraper** to your actors.
2. **Configure inputs** – Fill in the JSON input: set `maxItems`, `province`, `municipality`, filters, sorting, etc.
3. **Run the actor** – Click **Run** to begin scraping.
4. **Retrieve results** – View or download your data from the **Dataset** tab when the run completes.

## 💳 Pricing

On the **Free plan**, Apify provides $5 of free usage credits per month. Small-scale tests (up to a few hundred items) often fit within this limit.

For heavier usage, consider upgrading:

- **Personal Plan ($49/month)**: Higher request quotas and parallel runs.
- **Business Plans**: Custom limits, enterprise-level support, and SLAs.

## 📝 Input Parameters

Supply these inputs in JSON format to control your scrape:

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `maxItems` | integer | `10` | **Required.** Maximum number of properties to scrape (minimum `1`). |
| `province` | string | `""` | Province of the municipality (e.g., `RM` for Roma). If empty, auto-detected. |
| `municipality` | string | **Required** | Municipality (comuni) to search (e.g., `Roma`). |
| `area` | string | `""` | Area within the municipality (e.g., `Centro Storico`). Leave it empty and check the logs to see available areas. |
| `operation` | string | `buy` | Operation type: `buy`, `rent`, or `auction`. |
| `sortType` | string | `relevance` | Sort order: `relevance`, `minPrice`, `maxPrice`, `biggest`, `leastBig`, `mostRecent`, `leastRecent`, `maxRooms`, `minRooms`, `privateUsers`, `agencies`, `discounted`, `lessExpensiveM2`, `moreExpensiveM2`, `higherFloor`, `lowerFloor`. |
| `minPrice` | integer | `0` | Minimum price in EUR (`0` for any). |
| `maxPrice` | integer | `0` | Maximum price in EUR (`0` for any). |
| `minSize` | integer | `0` | Minimum size in m² (`0` for any). |
| `maxSize` | integer | `0` | Maximum size in m² (`0` for any). |
| `minRooms` | integer | `0` | Minimum number of rooms (`0` for any). |
| `maxRooms` | integer | `0` | Maximum number of rooms (`0` for any). |
| `bedrooms` | integer | `0` | Number of bedrooms (`0` for any). |
| `propertyCondition` | string | `""` | Condition: `newConstruction`, `excellent`, `good`, `toBeRenovated`. |
| `propertyType` | string | `""` | Type (buy/auction only): `apartment`, `house`, `commercialProperty`, `land`. |
| `floor` | array | `[]` | Building level: `ground`, `middle`, `last` (leave empty for any). |
| `garage` | array | `[]` | Garage: `singleGarage`, `doubleGarage`, `parkingSpace` (leave empty for any). |
| `hvac` | array | `[]` | HVAC: `autonomous`, `centralized`, `airConditioning` (leave empty for any). |
| `garden` | array | `[]` | Garden: `private`, `shared` (leave empty for any). |
| `energyRating` | string | `""` | Energy rating: `high`, `middle`, `low` (leave empty for any). |
| `terrace` | boolean | `false` | Whether the property has a terrace. |
| `balcony` | boolean | `false` | Whether the property has a balcony. |
| `lift` | boolean | `false` | Whether the property has a lift. |
| `cellar` | boolean | `false` | Whether the property has a cellar. |
| `pool` | boolean | `false` | Whether the property has a pool. |
| `furnished` | boolean | `false` | Whether the property is furnished. |
| `keywords` | array | `[]` | Keywords to include in the search (e.g., `"garage"`, `"terrazzo"`). |
| `excludeAuctions` | boolean | `false` | **Buy only:** Exclude auction listings. |
| `virtualTour` | boolean | `false` | Whether the property has a virtual tour. |
| `proxyConfiguration` | object | Apify Proxy | Proxy settings: `useApifyProxy` (`true`/`false`), `apifyProxyGroups` (e.g., `["RESIDENTIAL"]`). |

### Example input

```
{
  "maxItems": 60,
  "province": "RM",
  "municipality": "Roma",
  "area": "Centro",
  "operation": "buy",
  "sortType": "mostRecent",
  "minPrice": 200000,
  "maxPrice": 500000,
  "minSize": 50,
  "maxSize": 150,
  "minRooms": 2,
  "maxRooms": 4,
  "bedrooms": 2,
  "propertyCondition": "good",
  "propertyType": "apartment",
  "floor": ["middle"],
  "garage": ["parkingSpace"],
  "hvac": ["autonomous"],
  "garden": ["private"],
  "energyRating": "middle",
  "terrace": true,
  "balcony": true,
  "lift": true,
  "cellar": false,
  "pool": false,
  "furnished": false,
  "keywords": ["garage", "terrazzo"],
  "excludeAuctions": false,
  "virtualTour": false,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  }
}
```

## 📊 Output

The actor returns an array of property objects in JSON. Each object typically includes:

- **`id`, `uuid`, `title`, `creationDate`, `lastModified`**
- **`analytics`**: price, location (region, province, municipality, micro/macro-zone), typology, property status, advertiser, and features
- **`topology`**: surface (size, unit), rooms, bathrooms, floor, elevator, balcony, terrace, furnished
- **`price`**: display value, raw numeric, currency, discount
- **`geography`**: municipality, province, latitude, longitude, address details, zipcode
- **`media`**: images with `sd` and `hd` URLs and labels
- **`contacts`**: phone numbers, agency information
- **Additional fields**: badges, subProperties, inspections, etc.

Sample output fragment:

```
[
  {
    "id": 120063188,
    "uuid": "26bf6c3b-1b04-5061-b229-b515cf0b2685",
    "rty": "as",
    "title": "Apartment",
    "lastModified": 1754402065,
    "creationDate": 1745310056,
    "enabled": true,
    "analytics": {
      "price": "202500",
      "priceRange": "200.001 - 300.000 &euro;",
      "country": "Italia",
      "region": "Lazio",
      "province": "Rome",
      "macrozone": "Gregorio VII, Baldo degli Ubaldi",
      "microzone": "Gregorio VII - Piccolomini",
      "typology": "Appartamento",
      "category": "Residenziale",
      "contract": "vendita",
      "floor": "5",
      "numBedrooms": "1",
      "elevator": true,
      "advertiser": "agenzia",
      "propertyStatus": "Buono / Abitabile",
      "adVisibility": "premium",
      "agencyName": "Ius Brenta Aste",
      "agencyId": "413424",
      "otherFeatures": [
        "mansarda",
        "cucina",
        "balcone",
        "terrazzo",
        "parzialmente arredato",
        "esposizione doppia"
      ]
    },
    "contract": {
      "id": 1,
      "name": "Sale",
      "isHidden": false
    },
    "topology": {
      "typology": {
        "id": 4,
        "name": "Apartment"
      },
      "category": {
        "id": 1,
        "name": "Residential"
      },
      "surface": {
        "size": 86,
        "unitOfMeasure": "m²"
      },
      "isLuxury": false,
      "rooms": "5+",
      "bathrooms": "1",
      "floor": "5",
      "lift": true,
      "balcony": true,
      "terrace": true,
      "furnished": true
    },
    "price": {
      "value": "from € 202,500.00",
      "raw": 202500,
      "currency": "EUR",
      "isHidden": false,
      "startPrice": null,
      "discount": null
    },
    "geography": {
      "municipality": {
        "id": 6737,
        "name": "Rome"
      },
      "province": {
        "id": "RM",
        "name": "Rome"
      },
      "geolocation": {
        "latitude": 41.89595032,
        "longitude": 12.42983627,
        "visibilityType": "exact_location",
        "geoHash": "sr2y6fgj"
      },
      "zipcode": "00165",
      "street": "Via della Madonna del Riposo, 110, 00165 Roma RM, Italia, Roma - Roma, 110, 110",
      "macrozone": {
        "id": 10157,
        "name": "Gregorio VII, Baldo degli Ubaldi"
      },
      "microzone": {
        "id": 10825,
        "name": "Gregorio VII - Piccolomini"
      }
    },
    "badge": {
      "visibility": {
        "key": "isPremium",
        "label": "Premium",
        "opt": [
          {
            "label": "bgColor",
            "value": "#666666"
          }
        ]
      },
      "isNew": false,
      "isNewConstruction": false
    },
    "media": {
      "placeholder": null,
      "images": [
        {
          "sd": "https://pwm.im-cdn.it/image/1693993990/m-c.jpg",
          "hd": "https://pwm.im-cdn.it/image/1693993990/xxl.jpg",
          "label": "Zona"
        },
        {
          "sd": "https://pwm.im-cdn.it/image/1693994030/m-c.jpg",
          "hd": "https://pwm.im-cdn.it/image/1693994030/xxl.jpg",
          "label": "Cantina"
        }
      ]
    },
    "contacts": {
      "phones": [
        {
          "type": "tel1",
          "num": "+393280053019"
        }
      ],
      "bookVisitsEnabled": false,
      "agencyId": 413424,
      "agencyUuid": "d27e3b15-1c76-5423-8d88-f3cfa7e690e5"
    },
    "isUnread": false,
    "subProperties": null
  }
  // ...more listings
]
```

## 🌍 Proxy Configuration

To avoid IP blocks and geographic restrictions, Apify Proxy is supported:

- **useApifyProxy**: Set to `true` to enable.
- **apifyProxyGroups**: Choose one or more groups, e.g., `["RESIDENTIAL"]`.

## ⚖️ Legal & Ethics

Web scraping may be subject to Immobiliare.it’s terms of service, intellectual property rights, and data privacy laws (such as GDPR). Ensure you have a legitimate purpose, respect `robots.txt` directives, and comply with applicable regulations. When in doubt, seek legal advice.