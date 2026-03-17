## simple-pwa

Simple PWA setup in a vanilla HTML/CSS/JS website.<br>
Related to [cra-pwa](https://github.com/weaponsforge/cra-pwa) (React).

## Installation

> [!NOTE]
> This project uses `/simple-pwa` as a base path for GitHub Pages deployment.
> If running locally or deploying to a root domain, remove this prefix from all asset and service worker paths.

#### 1. Clone this repository.

```sh
git clone https://github.com/weaponsforge/simple-pwa.git
```

#### 2. Update asset paths.

If you're **not deploying to GitHub Pages**, update paths to remove `/simple-pwa`.

`manifest.json`
Update icon paths:

```json
{
  "name": "Simple PWA",
  "short_name": "PWA",
  "start_url": "/",
  "icons": [
    {
      "src": "/assets/web-app-manifest-192x192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/assets/web-app-manifest-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable any"
    }
  ],
  "theme_color": "#ffffff",
  "background_color": "#ffffff",
  "display": "standalone"
}
```

#### 3. Update service worker path.

`index.html`<br>
Ensure the service worker is registered from the root:

```javascript
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/sw.js')
  }
</script>
```

#### 4. Run locally.

- (a) Option 1: using `serve`.

   ```sh
   npx serve
   ```

- (b) Option 2: using Docker eg., with Windows PowerShell.

  > From the **parent** directory of the **root** project:

   ```sh
   docker run -it --rm -p 3000:3000 `
     -e PORT=3000 `
     -e USE_POLLING=true `
     -v ${pwd}/simple-pwa:/opt/app/public `
     weaponsforge/livereload-basic
   ```

## Resources

- [RealFaviconGenerator](https://realfavicongenerator.net/) - generates image and SVG favicons with a site.webmanifest file.
- [pwa-asset-generator](https://www.npmjs.com/package/pwa-asset-generator) - Offers a one-off execution that automatically generates icon and splash screen images, favicons and mstile images, and a JavaScript module that could be used programmatically for generating assets.

@weaponsforge<br>
20260317
