# Dummy Test Site

A static site packed with third-party scripts, iframes, images, and tracking pixels.
Use it to test the Truzyx consent widget tag-blocking on a page full of real-world
third-party resources.

## Hosting on GitHub Pages

1. Create a new GitHub repo (e.g. `truzyx-dummy-site`).
2. Copy `index.html` into the repo root.
3. Go to **Settings → Pages → Source** and select the `main` branch / root folder.
4. Your site will be live at `https://<username>.github.io/truzyx-dummy-site/`.

## Testing the consent widget

1. Publish a cookie template version in the Truzyx admin console.
2. Copy the `script_url` from the publish response.
3. Open the dummy site in Chrome.
4. Open **DevTools (F12) → Console** and run:

```js
const s = document.createElement("script");
s.src = "https://<your-cdn>/<templateId>";
s.async = true;
document.head.appendChild(s);
```

5. Verify that:
   - The consent banner and modal render correctly.
   - Third-party scripts/iframes/images that require consent are **blocked** (their `src` is stripped or they are replaced with `text/plain`).
   - After the user accepts a category, the blocked tags for that category are **unblocked** (fresh `<script>` elements are injected).
   - Consent is POSTed to the gateway's public consent endpoint.

## Third-party resources included

| # | Service | Domain | Cookie(s) |
|---|---------|--------|-----------|
| 1 | Google Analytics (gtag.js) | googletagmanager.com | `_ga`, `_gid` |
| 2 | Google Tag Manager | googletagmanager.com | — |
| 3 | Facebook Pixel | connect.facebook.net | `_fbp` |
| 4 | DoubleClick Ad | doubleclick.net | — |
| 5 | YouTube Embed | youtube.com | — |
| 6 | Twitter Widget | platform.twitter.com | — |
| 7 | LinkedIn Insight Tag | snap.licdn.com | — |
| 8 | Hotjar | static.hotjar.com | — |
| 9 | Microsoft Clarity | clarity.ms | — |
| 10 | Google AdSense | pagead2.googlesyndication.com | — |
| 11 | Google Analytics (tracking pixel) | google-analytics.com | — |
| 12 | Disqus | disqus.com | — |
| 13 | HubSpot | js.hs-analytics.net | — |
| 14 | Sentry | browser.sentry-cdn.com | — |
| 15 | Stripe.js | js.stripe.com | — |
| 16 | Google reCAPTCHA | google.com | — |
| 17 | Mixpanel | cdn.mxpnl.com | — |
| 18 | Segment | cdn.segment.com | — |
| 19 | Amplitude | cdn.amplitude.com | — |
| 20 | Braze (Appboy) | js.appboycdn.com | — |
