# Organization Schema Generator for SEO & GEO (2025 Edition)

## Overview

This guide provides a comprehensive framework for creating **perfect Organization schema markup** optimized for:

1. **Google Search** - Rich results, Knowledge Panels, brand disambiguation
2. **AI Search Engines** - ChatGPT, Perplexity, Gemini, Google AI Overview citations
3. **Entity Recognition** - Building the brand's semantic footprint across the web

**Last Verified**: December 30, 2025 against:
- [Google Search Central Documentation](https://developers.google.com/search/docs/appearance/structured-data/organization)
- [Schema.org Official Specifications](https://schema.org/Organization)
- GEO (Generative Engine Optimization) 2025 Best Practices

---

## Key 2025 Updates

### What's New from Google (December 2025)

1. **No Required Properties** - Google now recommends adding relevant properties rather than mandating specific ones
2. **ImageObject Support** - Logo can now be URL string OR ImageObject type
3. **Merchant Properties** - New support for `hasMerchantReturnPolicy`, `hasShippingService`, `hasMemberProgram`
4. **Disambiguation Focus** - Properties like `iso6523Code`, `naics`, `leiCode` help disambiguate organizations

### GEO Statistics (2025)

- **58%** of search queries now flow through AI-powered platforms (ChatGPT, Perplexity, Google AI)
- **30-40%** higher visibility in AI-generated answers for content with proper schema
- **85%** of enterprises increasing investment in structured data for AI search visibility

---

## Reference Template (Gold Standard)

Use this proven schema structure as your baseline:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "EmploymentAgency",
  "@id": "https://www.manpower.co.il/#organization",
  "name": "Manpower",
  "alternateName": "מנפאואר ישראל",
  "url": "https://www.manpower.co.il/",
  "logo": "https://www.manpower.co.il/logo.png",
  "description": "Manpower Israel is a leading employment agency providing staffing solutions, workforce management, and HR services across Israel since 1965.",
  "telephone": "+972-3-563-9999",
  "email": "info@manpower.co.il",
  "foundingDate": "1965",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "יגאל אלון 110",
    "addressLocality": "תל אביב-יפו",
    "postalCode": "6789149",
    "addressCountry": "IL"
  },
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+972-3-563-9999",
    "contactType": "customer service",
    "areaServed": "IL",
    "availableLanguage": ["he", "en"]
  },
  "sameAs": [
    "https://www.facebook.com/ManpowerIL",
    "https://www.instagram.com/manpower_israel/",
    "https://www.linkedin.com/company/manpower-israel/"
  ],
  "knowsAbout": [
    "Employment Services",
    "Staffing Solutions",
    "HR Management",
    "כוח אדם",
    "השמת עובדים"
  ],
  "areaServed": {
    "@type": "Country",
    "name": "Israel",
    "@id": "https://www.wikidata.org/wiki/Q801"
  },
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "minValue": 500,
    "maxValue": 1000
  }
}
</script>
```

---

## Schema Generation Rules

### 1. Choose the Most Specific @type

**CRITICAL**: Google recommends using the most specific Schema.org subtype. Never use generic "Organization" when a more specific subtype exists.

#### LocalBusiness Subtypes (Physical Locations)

| Business Type | Correct @type | Notes |
|---------------|---------------|-------|
| **Employment/HR Agency** | `EmploymentAgency` | Staffing, recruitment, HR services |
| **Medical/Health** | `MedicalBusiness` | General medical (see subtypes below) |
| **Integrative Medicine** | `MedicalBusiness` or `Physician` | NOT HomeAndConstructionBusiness |
| **Dentist** | `Dentist` | Subtype of MedicalBusiness |
| **Pharmacy** | `Pharmacy` | Subtype of MedicalBusiness |
| **Fitness/Gym** | `HealthClub` | Gyms, fitness centers, pilates studios |
| **Dive Center/Sports** | `SportsActivityLocation` | Scuba, surfing, sports centers |
| **Financial Services** | `FinancialService` | Banks, loans, mortgages, insurance |
| **Accounting** | `AccountingService` | Subtype of FinancialService |
| **Insurance** | `InsuranceAgency` | Subtype of FinancialService |
| **Educational** | `EducationalOrganization` | Schools, colleges, training centers |
| **Law Firm** | `LegalService` | Legal services, attorneys |
| **Real Estate** | `RealEstateAgent` | Property sales, rentals |
| **Construction** | `HomeAndConstructionBusiness` | Contractors, builders, fencing |
| **Beauty/Spa** | `BeautySalon`, `DaySpa`, `HairSalon` | Beauty services |
| **Restaurant/Cafe** | `Restaurant`, `Cafe`, `BarOrPub` | Food establishments |
| **Physical Store** | `Store` | Retail only (NOT for services) |
| **Hotel/Lodging** | `Hotel`, `LodgingBusiness` | Accommodation |
| **Travel Agency** | `TravelAgency` | Tour operators, travel booking |
| **Generic Services** | `ProfessionalService` | When no specific type fits |

#### MedicalBusiness Subtypes (26 Types)

Use the most specific medical type when applicable:

| Type | Use For |
|------|---------|
| `MedicalClinic` | General clinics |
| `Physician` | Doctor's office, integrative medicine |
| `Dentist` | Dental services |
| `Pharmacy` | Pharmacies |
| `Optician` | Eye care, glasses |
| `Physiotherapy` | Physical therapy |
| `Psychiatric` | Mental health |
| `Pediatric` | Children's health |
| `Dermatology` | Skin care |
| `Oncologic` | Cancer treatment |

#### FinancialService Subtypes

| Type | Use For |
|------|---------|
| `FinancialService` | General financial services, mortgages, loans |
| `AccountingService` | Accountants, bookkeeping |
| `BankOrCreditUnion` | Banks |
| `InsuranceAgency` | Insurance providers |

#### Non-LocalBusiness Types

| Business Type | Correct @type | Notes |
|---------------|---------------|-------|
| Online Store Only | `OnlineStore` | No physical location |
| Corporation (large) | `Corporation` | Major companies |
| Non-Profit | `NGO` | Charities, foundations |
| Government | `GovernmentOrganization` | Government bodies |

### @type Selection Rules

1. **Physical location customers visit** → Use `LocalBusiness` or its subtypes
2. **Purely online business** → Use `OnlineStore` or `OnlineBusiness`
3. **Service-based without storefront** → Use `ProfessionalService`
4. **Multiple types** → Use array format: `"@type": ["Electrician", "Plumber"]`

---

### 2. Common @type Mistakes to AVOID

| Wrong | Correct | Why |
|-------|---------|-----|
| `Store` for financial services | `FinancialService` | Store is for retail products only |
| `HomeAndConstructionBusiness` for medical | `MedicalBusiness` | Medical services need medical types |
| `TravelAgency` for dive center | `SportsActivityLocation` | Sports activities, not travel booking |
| `Organization` for any business | Specific subtype | Always use most specific type |
| Generic `LocalBusiness` | Specific subtype | 30+ subtypes available |

---

### 3. Logo Requirements (CRITICAL)

**Google Requirements:**
- **Minimum size**: 112x112 pixels
- **Recommended**: 200x200 pixels or larger
- **Must be crawlable** and indexable by Googlebot
- **Display well on white background** (Google may show on white)

**Format Preference:**
1. **PNG** - Best for logos with transparency (Recommended)
2. **JPG/JPEG** - Good for photos
3. **SVG** - Accepted but PNG/JPG preferred for maximum compatibility
4. **ICO** - NOT recommended (favicon format)
5. **WebP** - Accepted

**Common Mistakes:**
- Using 32x32 favicon instead of full logo
- Using .ico files
- Logo URL returning 404
- Logo blocked by robots.txt

**Example:**
```json
"logo": "https://example.com/images/logo-full-size.png"
```

Or with ImageObject for additional properties:
```json
"logo": {
  "@type": "ImageObject",
  "url": "https://example.com/images/logo.png",
  "width": 300,
  "height": 200
}
```

---

### 4. Essential Properties (Always Include)

```json
{
  "@context": "https://schema.org",
  "@type": "[SPECIFIC_TYPE]",
  "@id": "[URL]/#organization",
  "name": "[Official Business Name]",
  "url": "[Website URL with https://]",
  "logo": "[Logo URL - minimum 112x112px, PNG/JPG preferred]",
  "telephone": "[+country-code-number format]",
  "description": "[150-300 character business description - CRITICAL FOR GEO]",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[Street Address]",
    "addressLocality": "[City]",
    "postalCode": "[Postal Code]",
    "addressCountry": "[2-letter ISO code: IL, US, GB, etc.]"
  }
}
```

---

### 5. Recommended Properties

#### For Brand Recognition & SEO:
```json
{
  "alternateName": "[Alternative name, Hebrew name, acronym]",
  "legalName": "[Full registered legal name if different]",
  "slogan": "[Company tagline if exists]",
  "foundingDate": "1998",
  "email": "info@example.com"
}
```

#### For Contact & Service:
```json
{
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+972-3-XXX-XXXX",
    "contactType": "customer service",
    "areaServed": "IL",
    "availableLanguage": ["he", "en"],
    "contactOption": "TollFree"
  }
}
```

**contactType Values:**
- `customer service` - General inquiries
- `technical support` - Tech help
- `billing support` - Payment issues
- `sales` - Sales department

#### For Social & Entity Linking (sameAs):
```json
{
  "sameAs": [
    "https://www.facebook.com/[page]",
    "https://www.instagram.com/[handle]/",
    "https://www.linkedin.com/company/[company]/",
    "https://twitter.com/[handle]",
    "https://www.youtube.com/@[channel]",
    "https://he.wikipedia.org/wiki/[page]",
    "https://www.wikidata.org/wiki/[Q-number]"
  ]
}
```

#### For Trust Signals:
```json
{
  "vatID": "[VAT/Company Number]",
  "taxID": "[Tax ID if different]",
  "leiCode": "[Legal Entity Identifier - ISO 17442]",
  "iso6523Code": "[ISO 6523 identifier]",
  "naics": "[NAICS industry code]",
  "duns": "[DUNS number if available]"
}
```

---

### 6. GEO Optimization Properties (AI Search)

**CRITICAL for AI search visibility:**

#### knowsAbout (Expertise Areas):
```json
{
  "knowsAbout": [
    "Employment Services",
    "Staffing Solutions",
    "HR Management",
    {
      "@type": "Thing",
      "name": "Human Resources",
      "sameAs": "https://en.wikipedia.org/wiki/Human_resources"
    }
  ]
}
```

**Best Practice**: Include both plain text and Thing objects with Wikipedia/Wikidata links for better entity recognition.

#### areaServed (Service Areas):
```json
{
  "areaServed": {
    "@type": "Country",
    "name": "Israel",
    "@id": "https://www.wikidata.org/wiki/Q801"
  }
}
```

Or multiple areas:
```json
{
  "areaServed": [
    {
      "@type": "City",
      "name": "Tel Aviv",
      "@id": "https://www.wikidata.org/wiki/Q33935"
    },
    {
      "@type": "City",
      "name": "Jerusalem",
      "@id": "https://www.wikidata.org/wiki/Q1218"
    }
  ]
}
```

#### @id Property (Entity Disambiguation):
```json
{
  "@id": "https://www.example.com/#organization"
}
```

This creates a unique identifier that helps search engines and AI understand this is a distinct entity.

---

### 7. LocalBusiness Additional Properties

If using `LocalBusiness` or its subtypes, ADD these:

```json
{
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday"],
      "opens": "09:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": "Friday",
      "opens": "09:00",
      "closes": "14:00"
    }
  ],
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 32.0853,
    "longitude": 34.7818
  },
  "priceRange": "$$"
}
```

**priceRange Values:**
- `$` or `₪` - Budget
- `$$` or `₪₪` - Moderate
- `$$$` or `₪₪₪` - Expensive
- `$$$$` or `₪₪₪₪` - Luxury

**geo Coordinates:**
- Latitude: Minimum 5 decimal places precision
- Longitude: Minimum 5 decimal places precision
- Get from Google Maps: Right-click on location → "What's here?"

---

### 8. Format & Validation Rules

1. **JSON-LD Format Only** - Always use `<script type="application/ld+json">`
2. **Phone Format**: International format `+972-X-XXX-XXXX`
3. **URL Format**: Include `https://` and trailing slash for homepage
4. **Logo**: Minimum 112x112px, PNG/JPG preferred
5. **Country Codes**: ISO 3166-1 alpha-2 (IL, US, GB, DE)
6. **Language Codes**: ISO 639-1 (he, en, ar, ru)
7. **No Trailing Commas**: Ensure valid JSON syntax
8. **Placement**: Homepage `<head>` section OR before `</body>`
9. **One Per Page**: Only need Organization schema on homepage/about page

---

## Information Gathering Checklist

### Essential (Must Have):
- [ ] Business name (official)
- [ ] Business name in Hebrew (if applicable)
- [ ] Website URL
- [ ] Logo URL (direct link, min 112x112px, PNG/JPG)
- [ ] Phone number
- [ ] Full address (street, city, postal code)
- [ ] Business type/industry

### Recommended:
- [ ] Social media links (Facebook, Instagram, LinkedIn)
- [ ] Email address
- [ ] Business description (2-3 sentences)
- [ ] Year founded
- [ ] Opening hours
- [ ] Languages supported
- [ ] Google Maps coordinates
- [ ] Company registration number

### GEO Enhancement:
- [ ] Areas/regions served
- [ ] Key services or specialties (for knowsAbout)
- [ ] Wikipedia page (if exists)
- [ ] Wikidata ID (if exists)
- [ ] Industry classification codes

---

## GEO-Specific Optimization Notes

For maximum AI search visibility:

1. **Description is CRITICAL** - This is what AI reads to understand and cite the business. Make it factual, specific, and information-dense.

2. **knowsAbout property** - Helps AI understand expertise areas. Use both plain text and Thing objects with Wikipedia links.

3. **sameAs links** - Builds entity recognition. Include Wikipedia/Wikidata for strongest entity signals.

4. **@id property** - Creates unique identifier for entity disambiguation.

5. **Consistent NAP** - Name, Address, Phone must match across all platforms.

6. **Specificity wins** - More specific @type = better AI understanding.

7. **Hebrew + English** - Include both for Israeli businesses (alternateName).

8. **Wikidata IDs** - Add @id links to Wikidata for areaServed and knowsAbout when possible.

---

## Validation Checklist Before Delivery

- [ ] Valid JSON syntax (no trailing commas, proper quotes)
- [ ] Most specific @type used (not generic Organization)
- [ ] @id property included
- [ ] All URLs complete with https://
- [ ] Phone in international format (+972...)
- [ ] Address includes country code
- [ ] Logo URL is direct link to image (min 112x112px)
- [ ] Logo is PNG/JPG (not ICO or small favicon)
- [ ] sameAs contains only active, real profiles
- [ ] Description is 150-300 characters, factual
- [ ] knowsAbout includes relevant expertise areas
- [ ] Ready for Rich Results Test validation

**Test URLs:**
- Google Rich Results Test: https://search.google.com/test/rich-results
- Schema Markup Validator: https://validator.schema.org/

---

## Quick Reference: Israeli Business Specifics

| Property | Format/Value |
|----------|--------------|
| Country Code | IL |
| Phone Format | +972-X-XXX-XXXX (remove leading 0) |
| Languages | ["he", "en"] minimum |
| Currency Symbol | ₪ for priceRange |
| Work Week | Sunday-Thursday (Friday short, Saturday closed) |
| VAT ID Format | 9-digit company number (ח.פ) |
| Wikidata Israel | Q801 |
| Wikidata Tel Aviv | Q33935 |
| Wikidata Jerusalem | Q1218 |

---

## Implementation Instructions

1. Generate schema following this guide
2. Validate at https://search.google.com/test/rich-results
3. Validate syntax at https://validator.schema.org/
4. Place in homepage `<head>` section OR before `</body>`
5. Verify in Google Search Console after indexing (Enhancements → Structured Data)
6. Monitor for errors in GSC

---

## Official Documentation Sources

- [Google Organization Schema](https://developers.google.com/search/docs/appearance/structured-data/organization)
- [Google LocalBusiness Schema](https://developers.google.com/search/docs/appearance/structured-data/local-business)
- [Schema.org Organization](https://schema.org/Organization)
- [Schema.org LocalBusiness](https://schema.org/LocalBusiness)
- [Schema.org MedicalBusiness](https://schema.org/MedicalBusiness)
- [Schema.org FinancialService](https://schema.org/FinancialService)
- [Schema.org EducationalOrganization](https://schema.org/EducationalOrganization)

---

*Last Updated: December 30, 2025*
*Verified against Google Search Central, Schema.org, and GEO 2025 Standards*
*Source: Nadav Digital SEO Agency (nadavon6@gmail.com)*
