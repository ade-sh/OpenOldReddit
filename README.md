# OpenOldReddit — Classic Old Reddit Chrome Extension

**OpenOldReddit** brings back the beloved, clean, and high-density **Old Reddit (`old.reddit.com`)** experience directly in your browser. It replaces Reddit's modern bloated interface with an authentic, fast, classic Old Reddit reader: high information density, classic blue headers, subreddit navigation bar, tabmenu sorting, rank numbers, vertical voting arrows, collapsible comment trees with `[–]` / `[+]` toggles, OP/Mod/Admin badges, and RES Night Mode support.

---

## Features

- **Authentic Old Reddit Design**:
  - Classic `#cee3f8` header and `#336699` navigation bar.
  - High-density listing layout with classic Verdana typography and post ranks (1, 2, 3...).
  - Domain sources displayed inline e.g. `(self.technology)` or `(github.com)`.
  - Flat action links: `comments`, `share`, `save`, `hide`, `report`.
- **Top Subreddit Bar & Classic Tabmenu**:
  - Top navigation strip with quick access to `POPULAR`, `ALL`, `RANDOM`, `ASKREDDIT`, `NEWS`, and user subscriptions.
  - Classic Old Reddit tabmenu sorting: `hot`, `new`, `rising`, `controversial`, `top`, `gilded`.
- **Vertical Voting Stack**:
  - Classic up/down arrows stacked vertically with net karma counts.
  - Authentic Reddit vote colors (`#ff4500` orangered upvote, `#7193ff` periwinkle downvote).
- **Classic Comment Trees**:
  - One-click `[–]` / `[+]` comment collapsing.
  - Clean author flairs and status badges: OP `[S]`, Moderator `[M]`, Admin `[A]`.
  - Classic comment action links: `permalink`, `save`, `reply`, `give award`.
- **RES Night Mode**:
  - Full dark theme inspired by Reddit Enhancement Suite (RES) Night Mode.
- **Built-in Media Viewer**:
  - Smooth preview and lightbox for images, galleries, and video streams.
- **Fast & Private**:
  - Operates locally via Chrome's same-origin session with Reddit.
  - No third-party servers, tracking, analytics, or external API keys required.
  - State and preferences persisted locally via `chrome.storage.local`.

---

## Install

The built extension files are located in **dist/**.

1. Open **chrome://extensions** in Google Chrome (or any Chromium-based browser like Brave, Edge, Vivaldi).
2. Turn on **Developer mode** in the top-right corner.
3. Click **Load unpacked** and select the **dist** folder of this repository.
4. Open or refresh any Reddit tab (`www.reddit.com`, `reddit.com`, or `old.reddit.com`).
5. Pin **OpenOldReddit** to your browser toolbar for quick toggling.

> **Toggle Note**: Click **Original Reddit** at the bottom left to return to native Reddit. Click the extension toolbar icon to reopen OpenOldReddit.

---

## Data & Permissions

- **Manifest V3**: Runs isolated content scripts on `www.reddit.com`, `reddit.com`, and `old.reddit.com`.
- **Security & Sandboxing**: The reader UI runs in an extension-origin iframe, keeping its styles completely separate from Reddit's DOM.
- **Permissions**: Only `storage` is requested to save your preferences, theme selection, and subreddit shortcuts.
- **Zero Telemetry**: All network operations use the active tab's native same-origin session. No data is ever transmitted to third parties.

---

## Development

Requires Node.js 24+.

### Setup & Build

```sh
# Install dependencies
npm ci

# Typecheck, run unit tests, and compile the production extension
npm run check
```

The extension bundle will be generated in `dist/`.

### Testing

```sh
# Run unit test suite
npm test

# Run browser smoke tests with Playwright (if Chromium is installed)
npm run test:browser
```

---

## Source Layout

- `src/client/` — Classic Old Reddit React UI, components, themes, and screens.
  - `src/client/components/PostCard.tsx` — Classic link listing item with vertical voting & rank.
  - `src/client/components/CommentRow.tsx` — Nested comment tree with `[–]` toggle & badges.
  - `src/client/components/RedditPanels.tsx` — Split and panel views.
  - `src/client/styles/theme.css` — Old Reddit color tokens & RES Night Mode styles.
  - `src/client/styles/reader.css` — High-density Old Reddit stylesheet.
- `src/shared/api.ts` — Reader presentation models and type definitions.
- `src/extension/` — Reddit normalization, content script, background service worker, and message bridge.
- `public/manifest.json` — Chrome Extension Manifest V3 configuration.
- `tools/build.mjs` — Extension build pipeline (Vite + Rollup).
