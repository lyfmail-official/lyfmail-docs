# Common Errors

## Deployment Issues

### "Failed to create deployment (status: 400)"

**Cause:** Missing `environment` block in GitHub Actions workflow.

**Fix:** Add this to your deploy job:
```yaml
environment:
  name: github-pages
  url: ${{ steps.deployment.outputs.page_url }}
```

### "Page not found" after deployment

**Cause:** GitHub Pages source not set to "GitHub Actions".

**Fix:** Go to **Settings → Pages** and select **GitHub Actions** as source.

## Service Worker Failures

### Service worker not registering

**Cause:** Missing HTTPS or incorrect scope.

**Fix:**
- Ensure site is served over HTTPS.
- Check `navigator.serviceWorker.register()` path.
- Verify manifest.json is valid.

### "Cache storage failed"

**Cause:** Storage quota exceeded.

**Fix:**
- Clear old caches in DevTools → Application → Cache Storage.
- Implement cache cleanup in service worker.

## Caching Problems

### Changes not reflecting after update

**Cause:** Aggressive caching by service worker or CDN.

**Fix:**
- Hard refresh: `Ctrl+Shift+R` (or `Cmd+Shift+R` on Mac).
- Unregister service worker in DevTools.
- Add cache-busting query parameters to assets.

## Build Failures

### "Node.js 20 actions are deprecated"

**Cause:** Using old action versions.

**Fix:** Update to latest versions:
```yaml
uses: actions/configure-pages@v5
uses: actions/deploy-pages@v4
```
```

---

