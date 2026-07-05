# Captivate (captivate-fm)

Captivate is a growth-oriented podcast hosting, distribution, and analytics platform. Its public REST API at `https://api.captivate.fm` lets developers authenticate a user, read and manage shows and their RSS feeds, create and update episodes, upload and search media (audio) files, and pull detailed listening analytics ("insights") at the podcast and episode level.

**Access model:** Public and self-serve. Any account holder generates a **user ID** and an **API token** from the API section of their Captivate account, then exchanges them at `POST /authenticate/token` for a **Bearer token** used on every other request. There is no partner application, sales gate, or approval step, and no separate API fee — API access is included with any active subscription. The API is documented as a public Postman collection at [docs.captivate.fm](https://docs.captivate.fm/).

**Transport:** The entire documented API is request/response REST over HTTPS. No public WebSocket or Server-Sent Events (streaming) surface is documented (see `review.yml`).

**Modeling note:** Every path, method, and request field below is transcribed directly from Captivate's live public Postman documentation. Captivate does not publish full JSON **response** schemas, so response bodies in the OpenAPI are modeled generically and flagged as such.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/captivate-fm/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/captivate-fm/refs/heads/main/apis.yml)

## Tags

- Podcasting
- Podcast Hosting
- Episodes
- Media
- Analytics
- RSS

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Captivate Users API

Authenticate a user with their user ID and API token to obtain a Bearer token, retrieve a user record, and list the shows a user can access or the shows a user manages or owns.

- **Base URL:** `https://api.captivate.fm`
- `POST /authenticate/token`, `GET /users/{id}`, `GET /users/{id}/shows`, `GET /users/{id}/shows/manager`

### Captivate Shows API

Read and update a show's metadata (title, description, categories, author, language, links), upload show artwork, and retrieve the show's public RSS feed URL.

- **Base URL:** `https://api.captivate.fm`
- `GET /shows/{id}/`, `PUT /shows/{id}`, `POST /shows/{id}/artwork`, `GET /shows/{id}/feed`

### Captivate Episodes API

List a show's published and scheduled episodes, read a single episode, and create or update episodes — linking uploaded media, show notes, season and episode numbers, publish date and status, and Apple Podcasts metadata.

- **Base URL:** `https://api.captivate.fm`
- `GET /shows/{id}/episodes`, `GET /shows/{id}/episodes/scheduled`, `GET /episodes/{id}`, `POST /episodes`, `PUT /episodes/{id}`

### Captivate Media API

Upload an audio media file to a show, retrieve a media record by ID, and list or search a show's media library with offset, order, and sort controls. Media is scoped to a single show and cannot be shared across shows.

- **Base URL:** `https://api.captivate.fm`
- `GET /media/{id}`, `POST /shows/{id}/media`, `GET /shows/{id}/media`, `GET /shows/{id}/media/search`

### Captivate Analytics API

Pull listening analytics (insights) for a podcast or a specific episode — overview, averages, all-time totals, month-by-month series, arbitrary date ranges broken down by location, browser, OS, device and episode, episode comparisons, and web-player analytics.

- **Base URL:** `https://api.captivate.fm`
- `GET /insights/{showId}/overview`, `.../averages`, `.../total`, `.../monthly`; `POST /insights/{showId}/range`, `.../compare`, `.../web-player/{episodeId}` (plus per-episode variants)

## Specifications

- [OpenAPI](openapi/captivate-fm-openapi.yml)
- [Postman Collection](collections/captivate-fm.postman_collection.json)
- [Open Collection](collections/captivate-fm.opencollection.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/captivate-fm)
- [Website](https://www.captivate.fm/)
- [Documentation](https://docs.captivate.fm/)
- [Support Documentation](https://help.captivate.fm/en/)
- [Status Page](https://status.captivate.fm)
- [Plans](plans/captivate-fm-plans-pricing.yml)
- [Rate Limits](rate-limits/captivate-fm-rate-limits.yml)
- [Fin Ops](finops/captivate-fm-finops.yml)

## Pricing (confirmed 2026-07-05)

| Plan | Monthly | Annual | Downloads/mo |
|------|---------|--------|--------------|
| Personal | $19 | $204 | 30,000 |
| Professional | $49 | $528 | 150,000 |
| Business | $99 | $1,080 | 300,000 |

All plans include every feature (API access, unlimited podcasts, unlimited team members, analytics, dynamic content insertion) and a 30-day free trial; tiers differ only by monthly download allowance.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
