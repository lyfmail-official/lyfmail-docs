# Performance Fixes

## Slow Load Times

### Diagnosis
Check in Chrome DevTools → Network:
- TTFB > 600ms → Server Issue
- Download time > 2s → File Size Issue
- Render blocking > 1s → Resource Issue

### Fixes

**Large images:**
```bash
# Convert to WebP
cwebp -q 85 image.jpg -o image.webp

# Create responsive sizes
convert image.jpg -resize 768x image-768.jpg
```

**Render-blocking resources:**
```html
<!-- Defer non-critical CSS -->
<link rel="preload" href="/css/main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="/css/main.css"></noscript>

<!-- Defer JavaScript -->
<script src="/js/analytics.js" defer></script>
```

## Large Bundle Sizes

### Analysis
```bash
# Check bundle size
npm run build
ls -la dist/

# Analyze with source map explorer
npx source-map-explorer dist/main.js
```

### Fixes
- Code splitting with dynamic imports.
- Tree shaking unused exports.
- Replace large libraries with lighter alternatives.

| Heavy Library | Lightweight Alternative |
|--------------|------------------------|
| Moment.js | date-fns |
| Lodash (full) | lodash-es (tree-shake) |
| jQuery | Vanilla JS |

## Render-Blocking Resources

**Critical CSS inline:**
```html
<style>
  /* Above-the-fold CSS */
  body{margin:0;font-family:system-ui}
  .hero{min-height:100vh;display:flex;align-items:center}
</style>
<link rel="preload" href="/css/main.css" as="style" onload="this.rel='stylesheet'">
```

**Font loading:**
```css
@font-face {
  font-family: 'Inter';
  font-display: swap; /* Prevents invisible text */
  src: url('/fonts/inter.woff2') format('woff2');
}
