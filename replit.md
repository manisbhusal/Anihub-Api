# Anivexa API

An anime streaming aggregator API that resolves episode lists and stream URLs across 13 providers using a single AniList ID.

## How to run

The workflow `Start application` runs `PORT=5000 node server.js`. No build step or secrets required — start it from the Replit workflow panel.

## Stack

- Pure Node.js (ES modules), no framework, no dependencies
- Entry point: `server.js` → delegates to `index.js`
- Providers live in `providers/`
- API route handlers live in `api/`
- Core utilities in `core/`

## Routes

| Route | Description |
|---|---|
| `GET /map/:anilistId` | Cross-platform ID mappings (MAL, TVDB, TMDB, etc.) |
| `GET /episodes/:anilistId` | Episode lists from all providers |
| `GET /episodes/:provider[/:provider...]/:anilistId` | Filtered by provider(s) |
| `GET /watch/:provider/:anilistId/sub\|dub/:provider-:ep` | Stream URLs for one episode |
| `GET /stream/reanime/:id/sub\|dub/:ep` | 302 redirect to HLS stream |

## Notes

- Hosted on Replit with `PORT=5000` set in the workflow command
- Vercel is not recommended (shared IPs are blocked by most providers)
- The proxy in `proxy/` is for AniDB App, not for streams
