# SEO Audit Feedback — Gemora Assets

> **Audit date:** 13. feb 2026  
> **Auditor:** AI Code Assistant  
> **Status:** Needs optimization before production use

---

## 1. `robots.txt` — ✅ Good as-is

```
User-agent: *
Allow: /
Sitemap: https://gemora.dk/sitemap.xml
```

Simple and correct. No changes needed. Ready for `public/`.

---

## 2. `sitemap.xml` — ⚠️ Needs updates

### Issues
- **Missing `<lastmod>` dates** — Google prioritizes sitemaps with dates for crawl scheduling
- **Missing `<changefreq>`** — helps indicate how often content changes
- **Incomplete page list** — only 5 pages listed, but gemora.dk has more routes
- **Potentially dead URLs** — `/om-os` and `/kontakt` may not exist as live pages (verify before publishing)

### Recommended fix
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://gemora.dk/</loc>
    <lastmod>2026-02-13</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://gemora.dk/priser</loc>
    <lastmod>2026-02-13</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://gemora.dk/hvordan-det-virker</loc>
    <lastmod>2026-02-13</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://gemora.dk/privatlivspolitik</loc>
    <lastmod>2026-02-13</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.3</priority>
  </url>
  <url>
    <loc>https://gemora.dk/databehandleraftale</loc>
    <lastmod>2026-02-13</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.3</priority>
  </url>
  <!-- Add /login, /signup only if you want them indexed -->
  <!-- Remove /om-os and /kontakt if they don't exist -->
</urlset>
```

---

## 3. `seo_metadata.json` — ⚠️ Needs work

### Issues per page

| Page | Issue |
|------|-------|
| **Home (`/`)** | H1 "Gemora giver lærere superkræfter" is catchy but lacks searchable keywords. Should include "AI" and "feedback" for search intent matching. |
| **Feedback (`/feedback`)** | Does this public landing page exist? If not, this entry is premature. |
| **Elevanalyse** | URL has typo: `/elevevanalyse` (double "e") — should be `/elevanalyse`. |
| **All pages** | Missing `og:title`, `og:description`, `og:image` for social sharing (Facebook, LinkedIn, Twitter). No `<title>` tags defined — only H1s. Title and H1 should be different! |

### Recommended structure
```json
{
  "pages": [
    {
      "url": "https://gemora.dk/",
      "title": "Gemora — AI-assistent til lærere i den danske skole",
      "h1": "Giv dine elever bedre feedback med AI",
      "meta_description": "Gemora hjælper danske lærere med at give dybere feedback, spare tid på rettelser og forstå hver elevs faglige behov — med sikker AI.",
      "og_image": "https://gemora.dk/og-image-home.png",
      "keywords": ["AI til lærere", "automatisk feedback", "opgaverettelse AI", "dansk skole AI"]
    },
    {
      "url": "https://gemora.dk/priser",
      "title": "Priser — Gemora AI til lærere",
      "h1": "Vælg den plan der passer til dig",
      "meta_description": "Kom i gang gratis eller vælg Pro/Ultra til ubegrænset AI-feedback. Se priser for individuelle lærere og skolelicenser.",
      "og_image": "https://gemora.dk/og-image-pricing.png",
      "keywords": ["Gemora pris", "AI undervisning pris", "skole AI licens"]
    },
    {
      "url": "https://gemora.dk/hvordan-det-virker",
      "title": "Sådan virker Gemora — AI-drevet undervisningsassistent",
      "h1": "Fra opgave til feedback på få minutter",
      "meta_description": "Se hvordan Gemora analyserer elevbesvarelser og giver personlig, handlingsorienteret feedback med AI — tilpasset den danske læseplan.",
      "og_image": "https://gemora.dk/og-image-how.png",
      "keywords": ["AI feedback skole", "automatisk rettelse", "Gemora demo"]
    }
  ]
}
```

---

## 4. `seo-guidelines.md` — ⚠️ Outdated

### Issues
- **Meta title too long:** `"Gemora - AI for lærere | Det Intelligente Klasseværelse"` = 58 chars — at the edge. Google truncates at ~60 characters.
- **H2/H3 suggestions don't match** the current landing page structure
- **Missing high-intent Danish keywords** that teachers actually search for:
  - *"AI til rettelser"*
  - *"automatisk feedback elever"*
  - *"opgaverettelse AI"*
  - *"AI undervisning Danmark"*
  - *"elevfeedback AI"*
- **No mention of** structured data (JSON-LD), Open Graph, or canonical URLs

### Recommended keyword targets (Danish)
| Keyword cluster | Search intent |
|----------------|---------------|
| AI til lærere / AI undervisning | Discovery — teachers exploring AI |
| Automatisk feedback / opgaverettelse AI | High intent — teachers looking for solutions |
| Elevanalyse AI / elevdata | Feature-specific — teachers comparing tools |
| Gemora | Brand — direct searches |

---

## 5. `SEO_automation_guide.md` — ℹ️ Premature

The guide covers Keywords Everywhere and DataForSEO APIs. While interesting for future automation, this is **premature** — focus on getting the basics right first:

1. ✅ Proper meta tags on all pages
2. ✅ `robots.txt` + `sitemap.xml` in production
3. ✅ Open Graph images for social sharing
4. ⬜ Structured data (JSON-LD `SoftwareApplication` + `EducationalOrganization`)
5. ⬜ Blog/content strategy for organic traffic
6. ⬜ Then consider API-driven keyword monitoring

---

## Priority Action Items

### 🔴 Do Now
1. Fix the sitemap with actual live routes + `lastmod` dates
2. Add `robots.txt` and `sitemap.xml` to `public/` folder
3. Set proper `<title>` and `<meta description>` on all landing pages
4. Fix the `/elevevanalyse` typo in metadata

### 🟡 Do Soon
5. Create Open Graph images (1200×630px) for social sharing
6. Add `og:title`, `og:description`, `og:image` meta tags
7. Add JSON-LD structured data for SaaS product
8. Submit sitemap to Google Search Console

### 🟢 Do Later
9. Start a blog targeting Danish teacher keywords
10. Set up keyword monitoring with DataForSEO/Keywords Everywhere
11. Add hreflang tags if expanding beyond Danish
