# Apex Browser

A browser shell for Android and desktop, with the rest of the suite built into it.

**Status: not built. This is the largest item in the plan, by a wide margin.**

## The choice you have to make first

There are two ways to build an Android browser and they are not close:

| | WebView | GeckoView |
| --- | --- | --- |
| Ships with Android | Yes | Extra ~50 MB per app |
| Ad blocking | Only by intercepting requests one at a time; no cosmetic filtering, slow | Real extensions, so uBlock Origin itself |
| Page engine | Chrome's, controlled by Google | Mozilla's, independent |
| Effort | An afternooon to start | Weeks just to make it stable |

If ad blocking is the reason for this product, WebView will disappoint you. Honest
ad blocking needs GeckoView and a bundled extension, and that carries its own maintenance
burden forever.

The desktop version is a separate codebase again (Tauri 2 wraps the system webview), so
"Android and desktop browser" is really two projects.

## What I would build first instead

A **reading shell**, not a browser: a page that takes a URL, renders it with your
`Apex Search` bar, and saves it to `Apex-Archive`. No tabs, no engine, no extension
system. That is a weekend, it is genuinely useful, and it tells you whether you actually
want the harder thing.

## What you need to do

1. Decide WebView or GeckoView. Nothing else can start until that is settled.
2. Decide whether the desktop half is in scope at all.

## First three steps

1. GeckoView with one bundled ad-blocking extension, loading a single page.
2. Downloads routed through `Apex-Shield` (which must exist first).
3. Bookmarks and history stored in Firestore, shared with `Apex-Archive`.
