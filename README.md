# Apex Browser

A browser shell for the suite.

**Status: the "reading shell" this README recommended building first is built and working.**
The Android browser (WebView or GeckoView) is still a decision you have to make, and it is
still the largest item in the plan.

## What is built

`index.html` is a dark, installable reading shell:

- **URL bar** that also takes search words. A bare domain opens as a page; anything else
  goes to a search engine you can change in `localStorage["apex-browser-search"]`
  (default DuckDuckGo; point it at your SearXNG base to keep searches private).
- **Back, forward, reload, home**, with the trail kept in memory for the session.
- **Pins** — the star keeps a page on the home grid, stored in this browser.
- **Recent** — last 50 pages you opened.
- **Honest fallback:** many sites send `X-Frame-Options: DENY` and will not render inside
  another page. The shell says so straight away and gives you **Open in a new tab**
  instead of showing a silent blank box.

## What it is not

It is not a browser engine. It cannot block ads, run extensions, keep tabs, download files
through Apex-Shield, or share history with Apex-Archive yet. Those need the Android shell
(GeckoView if ad blocking matters, WebView if it does not) and a desktop build with Tauri.

## Run it

```sh
python3 -m http.server 8080
```

Static files only. Deploy to Cloudflare Pages as-is; `_headers` already sets the CSP and
allows framing of remote pages.

## Next steps, in order

1. Decide WebView or GeckoView. Nothing on the Android side can start before that.
2. Route **★** into `Apex-Archive` (Firestore bookmark document) instead of `localStorage`.
3. Downloads through `Apex-Shield`, once that exists.
4. Reading mode: strip a fetched article to text and store it with the bookmark.
