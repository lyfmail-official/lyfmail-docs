# Cloudflare Pages Deployment

## Setup

1. Connect your GitHub repository to Cloudflare Pages.
2. Select `lyfmail-docs` repository.
3. Configure build settings:

| Setting | Value |
|---------|-------|
| Framework preset | None |
| Build command | (leave empty) |
| Build output directory | `.` |

## Custom Domain

1. Go to **Custom domains** in Cloudflare Pages dashboard.
2. Add `docs.example.com`
3. Update DNS records as instructed

## Environment Variables

None required for static documentation.

## Preview Deployments

Every pull request gets a unique preview URL automatically.

## Edge Features

- Enable **Auto Minify** for HTML/CSS/JS.
- Enable **Brotli** compression.
- Set **Browser Cache TTL** to 4 hours.
