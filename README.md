<div align="center">

<img src="docs/logo.svg" width="80" height="80"/>

# Anihubz API 2.2

**Anime streaming aggregator API — one endpoint, all your sources.**



</div>

---

## What is this?

A single API that aggregates anime episode lists and streaming links from multiple providers. Give it an AniList ID, get back everything — episodes, sources, and stream URLs — all in one place.

---

## Providers

| Provider         | Status     | Notes                                                                          |
| ---------------- | ---------- | ------------------------------------------------------------------------------ |
| **AllManga**     | ✅ Active  | Large Library                                                                  |
| **AnimePahe**    | ❌ Removed | Cloudflare JS Challenge — no reliable bypass                                   |
| **Reanime**      | ✅ Active  | Solid source for a wide range of titles                                        |
| **AniKoto**      | ✅ Active  | Good library, consistent                                                       |
| **AnimeGG**      | ✅ Active  | Fuzzy title matching + compact-query fix for sequels (e.g. Re:Zero S4)         |
| **AniNeko**      | ✅ Active  | Reliable slug-based matching                                                   |
| **AniDB App**    | ✅ Active  | Language-aware, AniDB ID backed                                                |
| **AniZone**      | ✅ Active  | HLS + subtitles, sub-only; year-based re-scoring prevents wrong-season matches |
| **2dhive**       | ✅ Active  | Uses MAL ID internally; AniList ID used everywhere else                        |
| **Anibd**        | ✅ Active  | Uses Anilist ID internally; AniList ID used everywhere else                    |
| **Kickassanime** | ✅ Active  | Fuzzy search, medium library                                                   |
| **AnimeDunya**   | ✅ Active  | HLS + subtitles, sub-only, MAL ID backed                                       |

---

## Routes

```
GET /map/:anilistId
```

Returns cross-platform ID mappings — MAL, TVDB, TMDB, Kitsu, AniDB, and more.

```
GET /episodes/:anilistId
GET /episodes/:provider[/:provider...]/:anilistId
```

Returns episode lists in a single response with smart background refresh. Pass one or more provider names in the path to filter results — e.g. `/episodes/anizone/allmanga/16498` returns only those two. Omit providers to get all of them.

```
GET /watch/:provider/:anilistId/sub|dub/:provider-:ep
```

Returns stream URLs for a specific episode from a specific provider.

```
GET /stream/reanime/:id/sub|dub/:ep
```

302 redirect directly to the HLS stream.

---

## Self-hosted

```bash
git clone https://github.com/manisbhusal/Anihub-Api
cd Anihub-API
node server.js
```

Runs on Node.js. No build step needed.

---

## Deploying on Vercel

> ⚠️ **Not recommended.** Vercel runs on shared datacenter IPs that are widely blocked by anime streaming sites. Most providers will fail silently or return errors — the API will technically run but you'll get little to no data back. Use a self-hosted VPS or use railway, render etc etc. The proxy file is for anidb app not for streams!

---

## Contributing

> **Only request providers that self-host their content. No scrapers of third-party sites.**

Got a provider you'd like added? Open an issue or drop it in the Discord.

This project is community-kept-alive — if it helps you, please:

- ⭐ **Star the repo** so others can find it
- 💬 **[Join the Discord](https://discord.gg/Gtk2B2dz5c)** to discuss, report issues, or suggest providers
- 🛠️ **Open a PR** if you want to add or fix something

---

<div align="center">

hope it helped :3

[![Discord](https://img.shields.io/badge/Join%20the%20community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/MARQ9z9QSX)

</div>
