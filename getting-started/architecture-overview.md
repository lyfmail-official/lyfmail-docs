# Architecture Overview

## Subdomain Model

LYF Mail uses a strategic subdomain architecture for targeted SEO, content organization, and independent scaling:

```
lyfmail.com (Main Hub)
├── app.lyfmail.com (PWA)
├── docs.lyfmail.com (Documentation)
├── *.signup.lyfmail.com (Newsletter Landings)
├── *.lyfmail.com (Tools & Apps)
└── support.lyfmail.com (Help Center)
```

## CDN Strategy

- Static assets served via Cloudflare CDN.
- Edge caching for documentation pages.
- DDoS protection and SSL termination.

## Edge Deployment

- GitHub Pages for open-source documentation.
- Cloudflare Pages for high-traffic tools.
- VPS with Nginx for custom backend needs.

## Zero-Backend Architecture

Many LYF Mail tools use:
- **localStorage** for user preferences.
- **IndexedDB** for offline data.
- **Web Crypto API** for client-side encryption.
- **Service Workers** for offline functionality.
