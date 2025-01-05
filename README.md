# Brand.dev API SDK

Welcome to the official Brand.dev API SDK for TypeScript!

The Brand.dev SDK provides a simple way to interact with the Brand.dev API to fetch your brand data programmatically. Use this SDK to fetch brand data such as logos, colors, backdrops, descriptions, social media links, and more.

## Quick Start

### Step 1: Set Up Your Brand.dev Account

Sign up for a Brand.dev account.

Retrieve your API key from the Brand.dev Developer Dashboard.

### Step 2: Install the SDK

Install the SDK using npm:

```
npm install @branddev/typescript-sdk
```

### Step 3: Use the SDK

#### A. Fetching Brand Data for a Domain

```typescript
import { BrandDevApi } from "@branddev/typescript-sdk";

const brandDevApi = new BrandDevApi({ accessToken: "your_api_key_here" });

async function fetchBrandData() {
  const brandData = await brandDevApi.brandRetrieveGet({ domain: "brand.dev" });
  console.log({ brandData: brandData.data });
}

fetchBrandData();
```

Result will look like this:

```json
{
  "status": "ok",
  "brand": {
    "domain": "brand.dev",
    "title": "Brand.dev",
    "description": "The company offers a powerful API designed for customizing online experiences by enabling users to retrieve essential branding elements such as logos, colors, fonts, and more from any domain in just seconds. By providing seamless access to these brand assets, the company empowers developers and businesses to enhance their websites and applications with consistent and visually appealing designs tailored to their specific brand identity. This innovative solution simplifies the process of brand management and ensures that users can quickly integrate customized visual elements, improving both user experience and overall brand coherence.",
    "slogan": "Customize online experiences with logos, colors, fonts via API.",
    "colors": [
      {
        "hex": "#bc6cf4",
        "name": "Queer Purple"
      }
    ],
    "logos": [
      {
        "url": "https://media.brand.dev/144b5880-2ac3-469a-b705-cf5f2ddbb1cf.png",
        "mode": "dark",
        "group": 2,
        "colors": [
          {
            "hex": "#bc6cf4",
            "name": "Queer Purple"
          }
        ],
        "resolution": {
          "width": 500,
          "height": 500
        }
      },
      {
        "url": "https://media.brand.dev/f0cfd771-9361-4490-8571-68cb36e5872c.jpg",
        "mode": "dark",
        "group": 1,
        "colors": [
          {
            "hex": "#c384f2",
            "name": "Azuremyst Isle"
          }
        ],
        "resolution": {
          "width": 48,
          "height": 48
        }
      }
    ],
    "backdrops": [
      {
        "url": "https://media.brand.dev/bddfdc9e-b81d-4d12-a4ac-a41f9dd826c9.jpg",
        "colors": [
          {
            "hex": "#ba75f0",
            "name": "Illicit Purple"
          },
          {
            "hex": "#ece4f3",
            "name": "Tranquil Eve"
          },
          {
            "hex": "#110e15",
            "name": "Ruined Smores"
          }
        ],
        "resolution": {
          "width": 1200,
          "height": 400
        }
      },
      {
        "url": "https://media.brand.dev/fa550b6b-ac8b-4415-8ee8-fa5e9eaf6b94.jpg",
        "colors": [
          {
            "hex": "#b473e8",
            "name": "Lavender"
          },
          {
            "hex": "#ebdff1",
            "name": "Divine Dove"
          },
          {
            "hex": "#0e0a11",
            "name": "Black Sheep"
          }
        ],
        "resolution": {
          "width": 1128,
          "height": 191
        }
      }
    ],
    "address": null,
    "socials": [
      {
        "type": "x",
        "url": "https://x.com/get_brand_dev"
      },
      {
        "type": "linkedin",
        "url": "https://linkedin.com/company/branddev"
      }
    ],
    "verified": false,
    "stock": null,
    "fonts": [
      {
        "usage": "title",
        "name": "Inter"
      },
      {
        "usage": "body",
        "name": "DM Sans"
      },
      {
        "usage": "button",
        "name": "sans-serif"
      }
    ]
  },
  "code": 200
}
```

#### B. Searching for Brand Data

```typescript

import { BrandDevApi } from "@branddev/typescript-sdk";

const brandDevApi = new BrandDevApi({ accessToken: "your_api_key_here" });

async function searchBrands() {
  const brandSearch = await brandDevApi.brandSearchGet({
    query: "meta",
  });
  console.log({ brandSearch: brandSearch.data });
}

searchBrands();
```

Result will look like this:

```json
[
  {
    "logo": "https://media.brand.dev/3e780cb5-5745-4d6c-a9c2-c15441b9e87b.png",
    "title": "Meta Platforms, Inc.",
    "domain": "meta.com"
  },
  {
    "logo": "https://media.brand.dev/7df9e441-4a01-44ff-bd8b-9ba1e742f740.png",
    "title": "PT Meta Epsi Tbk.",
    "domain": "metaepsi.com"
  },
  {
    "logo": "https://media.brand.dev/11940626-d3ba-4773-9d13-e9abb6c1a554.png",
    "title": "Meta Corporation Public Company Limited",
    "domain": "metacorporation.co.th"
  },
  {
    "logo": "https://media.brand.dev/3e786c9a-4eaa-4e6f-a6b6-2e0e7961ceaf.png",
    "title": "Meta Data Limited",
    "domain": "ir.onesmart.org"
  },
  {
    "logo": "https://media.brand.dev/efdf90a5-f113-4d0e-8fa9-3d15db2c4f38.png",
    "title": "Meta Materials Inc. (META®)",
    "domain": "metamaterial.com"
  },
  {
    "logo": "https://media.brand.dev/e61851cf-2baa-4e57-9289-e4dca685fced.png",
    "title": "Liquid Meta Capital Holdings Ltd.",
    "domain": "liquidmeta.io"
  },
  {
    "logo": "https://media.brand.dev/cce4ce40-eb08-430b-a46d-2dbab9aef369.png",
    "title": "Meta",
    "domain": "meta.ai"
  },
  {
    "logo": "https://media.brand.dev/546758a1-11da-43a5-a1b0-29b0df029087.png",
    "title": "Meta",
    "domain": "gometa.com"
  },
  {
    "logo": "https://media.brand.dev/cc261d33-581d-45fb-9ab7-e856890cb4e2.png",
    "title": "Meta",
    "domain": "metacaresolutions.com"
  }
]
```

#### C. Classifying Brands by NAICS Code

```typescript
import { BrandDevApi } from "@branddev/typescript-sdk";

const brandDevApi = new BrandDevApi({ accessToken: "your_api_key_here" });

async function getBrandNaics() {
  const brandNaics = await brandDevApi.brandNaicsGet({
    input: "gregorys coffee",
  });
  console.log({ brandNaics: brandNaics.data });
}

getBrandNaics();
```

Result will look like this:

```json
{
  "domain": "gregoryscoffee.com",
  "codes": [
    {
      "code": "311920",
      "name": "Coffee and Tea Manufacturing"
    },
    {
      "code": "445298",
      "name": "All Other Specialty Food Retailers"
    }
  ],
  "type": "naics",
  "status": "ok"
}
```

#### D. Extracting Brand Data from Transactions

```typescript
import { BrandDevApi } from "@branddev/typescript-sdk";

const brandDevApi = new BrandDevApi({ accessToken: "your_api_key_here" });

async function identifyBrandFromTransaction() {
  const brandTransactionIdentifier = await brandDevApi.brandTransactionIdentifierGet({
    transactionInfo: "GREGORYS COFFEE $9.99",
  });
  console.log({ brand: brandTransactionIdentifier.data.brand });
}

identifyBrandFromTransaction();
```

Result will look like this:

```json
{
  "status": "ok",
  "brand": {
    "domain": "gregoryscoffee.com",
    "title": "Gregorys Coffee",
    "description": "Gregorys Coffee is a rapidly expanding specialty coffee brand with a focus on integrating lifestyle and wellness into their growing network of cafes across the NorthEast, specifically in New York, New Jersey, and Washington, D.C. Their mission is to build a community of individuals who view coffee in a unique way. With an emphasis on quality, innovation, and exceptional service, Gregorys Coffee offers customers a blend of the artisanal coffee shop experience with the convenience and efficiency of chain establishments. Customers can now purchase Gregorys Coffee online for home delivery, allowing them to enjoy their favorite brews at any time.",
    "slogan": "See Coffee Differently",
    "colors": [
      {
        "hex": "#7c7c7c",
        "name": "Namara Grey"
      },
      {
        "hex": "#080808",
        "name": "Reversed Grey"
      },
      {
        "hex": "#c6c6c6",
        "name": "Silver Polish"
      }
    ],
    "logos": [
      {
        "url": "https://media.brand.dev/329b806d-39dd-4ddc-8585-2ad174de653b.png",
        "mode": "dark",
        "group": 3,
        "colors": [
          {
            "hex": "#7c7c7c",
            "name": "Namara Grey"
          },
          {
            "hex": "#050505",
            "name": "Black Metal"
          },
          {
            "hex": "#c2c2c2",
            "name": "Magnesium"
          }
        ],
        "resolution": {
          "width": 1500,
          "height": 1500
        }
      },
      {
        "url": "https://media.brand.dev/7414cce1-cda6-4afe-86d1-48986628e4af.png",
        "mode": "dark",
        "group": 4,
        "colors": [
          {
            "hex": "#7c7c7c",
            "name": "Namara Grey"
          },
          {
            "hex": "#0b0b0b",
            "name": "Raven"
          },
          {
            "hex": "#c8c8c8",
            "name": "Brushed Metal"
          }
        ],
        "resolution": {
          "width": 1418,
          "height": 1418
        }
      },
      {
        "url": "https://media.brand.dev/d41658e4-3653-4b8f-8043-fde826cbb636.jpg",
        "mode": "dark",
        "group": 1,
        "colors": [
          {
            "hex": "#7c7c7c",
            "name": "Namara Grey"
          },
          {
            "hex": "#080808",
            "name": "Reversed Grey"
          },
          {
            "hex": "#c6c6c6",
            "name": "Silver Polish"
          }
        ],
        "resolution": {
          "width": 320,
          "height": 320
        }
      },
      {
        "url": "https://media.brand.dev/8703d567-e1fe-40a7-ad41-df7ef16228b6.png",
        "mode": "light",
        "group": 5,
        "colors": [
          {
            "hex": "#040404",
            "name": "Armor Wash"
          }
        ],
        "resolution": {
          "width": 500,
          "height": 133
        }
      },
      {
        "url": "https://media.brand.dev/e7c73ebb-1243-459e-bebb-bbd5aa4bb280.png",
        "mode": "dark",
        "group": 6,
        "colors": [],
        "resolution": {
          "width": 280,
          "height": 277
        }
      },
      {
        "url": "https://media.brand.dev/823cd857-6993-4c9f-8ed9-1593cb8040a2.jpg",
        "mode": "dark",
        "group": 2,
        "colors": [
          {
            "hex": "#7c7c7c",
            "name": "Namara Grey"
          },
          {
            "hex": "#0d0d0d",
            "name": "Black Wash"
          },
          {
            "hex": "#d5d5d5",
            "name": "Disco Ball"
          }
        ],
        "resolution": {
          "width": 200,
          "height": 200
        }
      }
    ],
    "backdrops": [
      {
        "url": "https://media.brand.dev/fdeb8953-b7da-483c-813e-e74d5fac3851.jpg",
        "colors": [
          {
            "hex": "#764d31",
            "name": "Chocolate Bells"
          },
          {
            "hex": "#37363a",
            "name": "Sayward Pine"
          },
          {
            "hex": "#c2b2a5",
            "name": "Diverse Beige"
          }
        ],
        "resolution": {
          "width": 1012,
          "height": 337
        }
      },
      {
        "url": "https://media.brand.dev/f357d96e-2995-4fd0-a9d5-e2da7eadc67f.jpg",
        "colors": [
          {
            "hex": "#b24708",
            "name": "Beef Bourguignon"
          },
          {
            "hex": "#171413",
            "name": "Kokushoku Black"
          },
          {
            "hex": "#dedacf",
            "name": "Egret White"
          }
        ],
        "resolution": {
          "width": 1128,
          "height": 191
        }
      }
    ],
    "address": {
      "city": "New York City",
      "country": "UNITED STATES",
      "country_code": "US"
    },
    "socials": [
      {
        "type": "instagram",
        "url": "https://instagram.com/gregoryscoffee"
      },
      {
        "type": "tiktok",
        "url": "https://tiktok.com/@gregoryscoffee"
      },
      {
        "type": "facebook",
        "url": "https://facebook.com/gregoryscoffee"
      },
      {
        "type": "x",
        "url": "https://x.com/gregoryscoffee"
      },
      {
        "type": "linkedin",
        "url": "https://linkedin.com/company/gregorys-coffee"
      }
    ],
    "verified": false,
    "stock": null,
    "fonts": [
      {
        "usage": "title",
        "name": "GT Walsheim Pro Condensed !important"
      },
      {
        "usage": "body",
        "name": "GT Walsheim Pro Condensed !important"
      },
      {
        "usage": "button",
        "name": "GT Walsheim Pro Condensed !important"
      }
    ]
  },
  "code": 200
}
```

## Support

For support, visit the [Brand.dev Developer Portal](https://developer.brand.dev) or contact us at [yahia@brand.dev](mailto:yahia@brand.dev).
