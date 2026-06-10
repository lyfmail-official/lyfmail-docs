# Building Privacy-First PWAs

## Core Principles

1. **Data stays on device** — Use localStorage, IndexedDB, not cloud.
2. **No third-party trackers** — Self-host all analytics.
3. **Encryption by default** — Web Crypto API for sensitive data.
4. **Minimal permissions** — Only request what's essential.

## Local-First Architecture

```javascript
// Store data locally
const saveEntry = async (data) => {
  const db = await openDB('lyf-app', 1);
  await db.put('entries', {
    ...data,
    id: crypto.randomUUID(),
    createdAt: Date.now()
  });
};

// Sync when online
const syncWhenOnline = () => {
  window.addEventListener('online', async () => {
    const db = await openDB('lyf-app', 1);
    const unsynced = await db.getAllFromIndex('entries', 'syncStatus', 'pending');
    for (const entry of unsynced) {
      await syncToServer(entry);
      await db.put('entries', { ...entry, syncStatus: 'synced' });
    }
  });
};
```

## Web Crypto API

```javascript
// Generate encryption key
const generateKey = async () => {
  return crypto.subtle.generateKey(
    { name: 'AES-GCM', length: 256 },
    true,
    ['encrypt', 'decrypt']
  );
};

// Encrypt data
const encrypt = async (data, key) => {
  const encoder = new TextEncoder();
  const iv = crypto.getRandomValues(new Uint8Array(12));
  const encrypted = await crypto.subtle.encrypt(
    { name: 'AES-GCM', iv },
    key,
    encoder.encode(JSON.stringify(data))
  );
  return { iv, data: encrypted };
};
