# Manifest Configuration

## Basic manifest.json

```json
{
  "name": "LYF Mail App",
  "short_name": "LYF Mail",
  "description": "Privacy-first Digital Wellness Platform",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#0f172a",
  "theme_color": "#6366f1",
  "orientation": "portrait",
  "icons": [
    {
      "src": "assets/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "assets/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "any maskable"
    }
  ]
}
```

## Best Practices

- Use `maskable` icon purpose for adaptive icons.
- Keep `short_name` under 12 characters.
- Set `display: standalone` for app-like experience.
- Include `orientation` for mobile optimization.

## Testing

Use Chrome DevTools → Application → Manifest to validate.

