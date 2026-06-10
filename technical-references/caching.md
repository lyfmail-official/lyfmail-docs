# Caching Strategies

## Service Worker Caching

### Cache-First (Static Assets)
```javascript
const cacheFirst = async (request) => {
  const cached = await caches.match(request);
  if (cached) return cached;
  const response = await fetch(request);
  const cache = await caches.open('static-v1');
  cache.put(request, response.clone());
  return response;
};
```

### Network-First (Dynamic Content)
```javascript
const networkFirst = async (request) => {
  try {
    const networkResponse = await fetch(request);
    const cache = await caches.open('dynamic-v1');
    cache.put(request, networkResponse.clone());
    return networkResponse;
  } catch (error) {
    return caches.match(request);
  }
};
```

## CDN Configuration (Cloudflare)

### Page Rules
```
docs.example.com/static/*
  Cache Level: Cache Everything
  Edge Cache TTL: 1 month
  Browser Cache TTL: 1 month
```

### Cache Keys
- Include query string for versioned assets: `?v=1.2.3`
- Ignore query string for API calls

## Cache Invalidation

### Manual Purge
```bash
curl -X POST "https://api.cloudflare.com/client/v4/zones/{zone_id}/purge_cache" \
  -H "Authorization: Bearer {token}" \
  -H "Content-Type: application/json" \
  --data '{"files":["https://docs.lyfmail.com/index.html"]}'
```

### Versioned Filenames
Use content hashes in filenames:
```
main.a3f2b1c.css
app.9d8e7f6.js
