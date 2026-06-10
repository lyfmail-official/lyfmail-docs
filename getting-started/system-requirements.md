# System Requirements

## Browser Support

| Browser | Minimum Version | Notes |
|---------|----------------|-------|
| Chrome | 90+ | Full PWA Support |
| Firefox | 88+ | Service Worker Support |
| Safari | 14+ | iOS 14.5+ for PWA Install |
| Edge | 90+ | Chromium-based |
| Samsung Internet | 15+ | Android PWA Support |

## Server Requirements

For self-hosted deployment:

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| RAM | 512 MB | 1 GB |
| Storage | 100 MB | 500 MB |
| Bandwidth | 10 GB/month | Unmetered |
| HTTPS | Required | Required |

## Development Environment

- **Node.js**: 18+ (for build tools)
- **Python**: 3.8+ (for local server)
- **Git**: 2.30+

## Network Requirements

- HTTPS enabled (required for service workers).
- No strict CSP blocking inline scripts (for PWA manifest).
