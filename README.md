# Captivate (captivate-fm)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
