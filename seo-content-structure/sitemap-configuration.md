# Sitemap Configuration

## XML Sitemap Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://docs.example.com/</loc>
    <lastmod>2026-06-10</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://docs.example.com/getting-started/quick-start</loc>
    <lastmod>2026-06-10</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

## Multi-Subdomain Sitemaps

Create a sitemap index for all subdomains:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://lyfmail.com/sitemap.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://docs.lyfmail.com/sitemap.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://health.signup.example.com/sitemap.xml</loc>
  </sitemap>
</sitemapindex>
```

## Automation

Generate sitemaps dynamically:

```javascript
// Node.js example
const fs = require('fs');
const glob = require('glob');

const pages = glob.sync('**/*.md', { cwd: 'content' });
const sitemap = pages.map(page => ({
  url: `https://docs.lyfmail.com/${page.replace('.md', '')}`,
  lastmod: fs.statSync(`content/${page}`).mtime.toISOString().split('T')[0]
}));

// Generate XML...
```

Submit to Google Search Console and Bing Webmaster Tools.
