# Git Branching Diagram Maker

A lightweight, browser-based visual editor for creating and exporting git branching diagrams. No installation, no sign-up — runs entirely in your browser.

![Alpha](https://img.shields.io/badge/status-alpha-orange) ![License](https://img.shields.io/badge/license-MIT-blue)

## Features

- 🌿 **Interactive branch creation** — add branches at any commit, reorder them by dragging in the sidebar
- ➕ **Commit visualisation** — add commits to any branch and see the diagram update live
- 🔀 **Merge arrows** — click a commit, then a branch to draw a merge; supports solid, dashed, and dotted styles with optional labels
- 🏷️ **Commit tags** — annotate individual commits with tag badges
- 🎨 **Custom branch colours** — choose from a palette or pick any hex colour
- 🗑️ **Flexible deletion** — delete via click-then-Delete, area-drag selection, or the toolbar button
- 📤 **PNG export** — export your diagram as a high-resolution PNG
- ⌨️ **Keyboard shortcuts** — see below

## Usage

1. Open `index.html` in a modern web browser (no server required)
2. Click **⑂ Add Branch** to create a new branch from the currently selected one
3. Click **+ Add Commit** to add a commit to the selected branch
4. **Click a commit**, then click a branch line to draw a merge arrow
5. **Double-click** a branch name in the sidebar to rename it
6. **Drag** branches in the sidebar to reorder their vertical position
7. Click the **colour swatch** next to a branch to change its colour
8. Click **Export PNG** to download your diagram

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Delete` / `Backspace` | Delete selected commits, merges, or branch |
| `Escape` | Deselect / cancel current action |

## Browser Support

Requires a modern browser with ES module import map support:

| Browser | Minimum Version |
|---------|----------------|
| Chrome / Edge | 89+ |
| Firefox | 108+ |
| Safari | 16.4+ |

> Internet Explorer is not supported.

## Privacy

All diagram state is held in memory and lost on page refresh. No user-entered content is transmitted.

Anonymous page-view telemetry is sent via Microsoft Application Insights when `meta[name="app-insights-connection-string"]` in `index.html` contains a connection string. When the connection string is empty (the default), telemetry is completely disabled.

When enabled, the following privacy controls are applied:

- Sends a single page-view event per visit — no custom events, no exception tracking, no performance tracking
- Cookies disabled (`disableCookiesUsage`, `cookieCfg.enabled: false`)
- Browser storage disabled (`isStorageUseDisabled`)
- User, session, and device identifiers stripped from telemetry
- IP forced to `0.0.0.0` in the telemetry envelope
- Geolocation, browser fingerprint (`ext.web`), and OS (`ext.os`) fields stripped
- No AJAX, fetch, or correlation tracking
- No sign-in or user-entered diagram content is sent

The GitHub Actions workflow injects the connection string from a repository secret (`APP_INSIGHTS_CONNECTION_STRING`) at deploy time. Local development sends no telemetry.

Ensure Azure Application Insights IP masking remains enabled (the default) and review data retention settings for your deployment. If EU visitors are expected, host the Application Insights resource in an EU region to avoid cross-border data transfer concerns under GDPR.

## Development

Single-file application — all HTML, CSS, and JavaScript lives in `index.html`. Three.js is loaded from the jsDelivr CDN at runtime.

> **Status:** Alpha — the app is functional but may contain bugs or incomplete features.

## Third-Party Libraries

- [Three.js](https://threejs.org/) v0.162.0 — MIT License

## License

MIT © Joshua Harvey — see [LICENSE](LICENSE) for details.
