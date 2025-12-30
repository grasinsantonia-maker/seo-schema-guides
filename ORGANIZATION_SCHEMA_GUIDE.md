# Organization Schema Generator for SEO & GEO

## Overview

This guide provides a comprehensive framework for creating **perfect Organization schema markup** optimized for:

1. **Google Search** — Rich results, Knowledge Panels, brand disambiguation
2. **AI Search Engines** — ChatGPT, Perplexity, Gemini, Google AI Overview citations
3. **Entity Recognition** — Building the brand's semantic footprint across the web

---

## Reference Template (Gold Standard)

Use this proven schema structure from Manpower Israel as your baseline:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Manpower",
  "alternateName": "מנפאואר ישראל",
  "url": "https://www.manpower.co.il/",
  "logo": "https://www.manpower.co.il/_next/static/media/logo-manpower-white.b713aa15.svg",
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+972-3-563-9999",
    "contactType": "customer service",
    "areaServed": "IL",
    "availableLanguage": ["he", "en"]
  },
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "יגאל אלון 110",
    "addressLocality": "תל אביב-יפו",
    "postalCode": "6789149",
    "addressCountry": "IL"
  },
  "sameAs": [
    "https://www.facebook.com/ManpowerIL",
    "https://www.instagram.com/manpower_israel/",
    "https://www.linkedin.com/company/manpower-israel/"
  ]
}
</script>
```

---

## Schema Generation Rules

### 1. Choose the Most Specific @type

**CRITICAL**: Never use generic "Organization" when a more specific subtype exists.

| Business Type | Correct @type |
|---------------|---------------|
| Employment/HR Agency | `EmploymentAgency` |
| Physical Store/Shop | `Store` or specific (e.g., `ClothingStore`) |
| Restaurant/Cafe | `Restaurant`, `Cafe`, `BarOrPub` |
| Medical/Health | `MedicalBusiness`, `Dentist`, `Physician` |
| Fitness/Gym | `HealthClub`, `ExerciseGym` |
| Law Firm | `LegalService`, `Attorney` |
| Accounting | `AccountingService` |
| Real Estate | `RealEstateAgent` |
| Auto Service | `AutoRepair`, `AutoDealer` |
| Beauty/Spa | `BeautySalon`, `DaySpa`, `HairSalon` |
| Hotel/Lodging | `Hotel`, `BedAndBreakfast` |
| Online Store Only | `OnlineStore` |
| Corporation (large company) | `Corporation` |
| Non-Profit | `NGO` |
| Educational | `EducationalOrganization`, `School` |
| Generic Services | `LocalBusiness` or `ProfessionalService` |

**Rule**: If the business has a physical location customers visit → Use `LocalBusiness` subtypes
**Rule**: If purely online → Use `OnlineStore` or `OnlineBusiness`

---

### 2. Required Properties (Always Include)

These properties MUST be in every schema:

```json
{
  "@context": "https://schema.org",
  "@type": "[SPECIFIC_TYPE]",
  "name": "[Official Business Name]",
  "url": "[Website URL with https://]",
  "logo": "[Logo URL - minimum 112x112px, PNG/JPG preferred]",
  "telephone": "[+country-code-number format]",
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

### 3. Recommended Properties (Add When Available)

#### For Brand Recognition & SEO:
```json
{
  "alternateName": "[Alternative name, Hebrew name, acronym, etc.]",
  "description": "[150-300 character description of the business - CRITICAL FOR GEO]",
  "slogan": "[Company tagline if exists]",
  "foundingDate": "[YYYY format, e.g., 1998]",
  "email": "[Primary contact email]"
}
```

#### For Contact & Service:
```json
{
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "[Phone number]",
    "contactType": "customer service",
    "areaServed": "[Country code or array of regions]",
    "availableLanguage": ["he", "en", "ru", "ar"]
  }
}
```

#### For Social & Entity Linking:
```json
{
  "sameAs": [
    "https://www.facebook.com/[page]",
    "https://www.instagram.com/[handle]/",
    "https://www.linkedin.com/company/[company]/",
    "https://twitter.com/[handle]",
    "https://www.youtube.com/[channel]",
    "https://he.wikipedia.org/wiki/[page]"
  ]
}
```

#### For Trust Signals (Israeli Businesses):
```json
{
  "vatID": "[Israeli ח.פ / Company Number if available]",
  "taxID": "[Tax ID if different from VAT]",
  "legalName": "[Full registered legal name if different from name]"
}
```

#### For GEO/AI Optimization:
```json
{
  "knowsAbout": ["Topic 1", "Topic 2", "Service Area"],
  "areaServed": {
    "@type": "Country",
    "name": "Israel"
  },
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": 500
  }
}
```

---

### 4. LocalBusiness Additional Properties

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
    "latitude": "32.0853",
    "longitude": "34.7818"
  },
  "priceRange": "₪₪"
}
```

---

### 5. Format & Validation Rules

1. **JSON-LD Format Only** — Always use `<script type="application/ld+json">`
2. **Phone Format**: Always international format `+972-X-XXX-XXXX`
3. **URL Format**: Always include `https://` and trailing slash for homepage
4. **Logo Requirements**:
   - Minimum 112x112 pixels
   - Must be crawlable URL
   - Prefer PNG or JPG over SVG (some tools struggle with SVG)
5. **Country Codes**: Use ISO 3166-1 alpha-2 (IL, US, GB, DE, etc.)
6. **Language Codes**: Use ISO 639-1 (he, en, ar, ru, etc.)
7. **No Trailing Commas**: Ensure valid JSON syntax
8. **Placement**: Homepage `<head>` section OR before `</body>`

---

## Information Gathering Checklist

Before generating the schema, collect this information from the client:

### Essential (Must Have):
- [ ] Business name (official)
- [ ] Business name in Hebrew (if applicable)
- [ ] Website URL
- [ ] Logo URL (direct link to image file)
- [ ] Phone number
- [ ] Full address (street, city, postal code)
- [ ] Business type/industry

### Recommended (Request If Possible):
- [ ] Social media links (Facebook, Instagram, LinkedIn, etc.)
- [ ] Email address
- [ ] Business description (2-3 sentences)
- [ ] Year founded
- [ ] Opening hours
- [ ] Languages spoken/supported
- [ ] Google Maps coordinates (latitude/longitude)
- [ ] Company registration number (ח.פ)

### Optional (Enhances Schema):
- [ ] Slogan/tagline
- [ ] Number of employees (approximate)
- [ ] Areas/regions served
- [ ] Key services or specialties
- [ ] Wikipedia page (if exists)
- [ ] Other directory listings

---

## GEO-Specific Optimization Notes

For maximum AI search visibility:

1. **Description is CRITICAL** — This is what AI reads to understand and cite the business
2. **knowsAbout property** — Helps AI understand the business's expertise areas
3. **sameAs links** — Builds entity recognition across platforms
4. **Consistent NAP** — Name, Address, Phone must match across all platforms
5. **Specificity wins** — More specific @type = better AI understanding
6. **Hebrew + English** — Include both for Israeli businesses (alternateName)

---

## Validation Checklist Before Delivery

- [ ] Valid JSON syntax (no trailing commas, proper quotes)
- [ ] Most specific @type used
- [ ] All URLs are complete with https://
- [ ] Phone in international format
- [ ] Address includes country code
- [ ] Logo URL is direct link to image
- [ ] sameAs contains only active, real profiles
- [ ] Description is 150-300 characters
- [ ] Ready for Rich Results Test validation

**Test URL**: https://search.google.com/test/rich-results

---

## Quick Reference: Israeli Business Specifics

| Property | Format/Value |
|----------|--------------|
| Country Code | IL |
| Phone Format | +972-X-XXX-XXXX (remove leading 0) |
| Languages | ["he", "en"] minimum, add ["ru", "ar", "am"] as applicable |
| Currency Symbol | ₪ for priceRange |
| Work Week | Sunday-Thursday (Friday short day, Saturday closed typically) |
| VAT ID Format | 9-digit company number (ח.פ) |

---

## Implementation Instructions

1. Generate schema following this guide
2. Validate at https://search.google.com/test/rich-results
3. Place in homepage `<head>` section OR before `</body>`
4. Verify in Google Search Console after indexing

---

*Last Updated: December 2025*
*Optimized for Google's Organization schema documentation and GEO research for AI search optimization.*
*Source: Nadav Digital SEO Agency (nadavon6@gmail.com)*
