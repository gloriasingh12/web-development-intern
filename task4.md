# PWA E-Commerce Platform (Task 63)

### 1. Service Worker Logic (`sw.js`)
*This script handles offline functionality and caching.*
```javascript
const CACHE_NAME = "v1_soit_shop";
const assets = ["/", "/index.html", "/styles.css", "/app.js"];

// Install Service Worker
self.addEventListener("install", (e) => {
  e.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      return cache.addAll(assets);
    })
  );
});

// Fetch Assets Offline
self.addEventListener("fetch", (e) => {
  e.respondWith(
    caches.match(e.request).then((res) => {
      return res || fetch(e.request);
    })
  );
});
