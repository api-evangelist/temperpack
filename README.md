# TemperPack

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

TemperPack is a Richmond, Virginia based sustainable packaging manufacturer, founded in 2015 and a Certified B Corporation, that designs and manufactures curbside recyclable and compostable alternatives to expanded polystyrene (EPS) and single-use plastic for cold chain and protective shipping.

Three material platforms — **ClimaCell** (starch-and-paper thermal liners), **Green Cell Foam** (certified compostable starch insulation) and **WaveKraft** (on-demand paper cushioning) — are manufactured in ISO 9001:2015 certified plants in Richmond VA, Lansing MI and Las Vegas NV, with in-house ISTA thermal and mechanical testing at the Proving Ground lab. Customers span life sciences, food and beverage, pet and veterinary, wine, and packaging distribution.

## API surface

**TemperPack publishes no public API** as of August 2026. The full contract-discovery sweep is recorded in
[`well-known/temperpack-well-known.yml`](well-known/temperpack-well-known.yml): no OpenAPI/Swagger, no
GraphQL, no MCP server, no A2A agent card, and no `/.well-known/` documents on any host. `api.`,
`developer.` and `docs.temperpack.com` do not resolve.

What TemperPack does run is a **customer portal** (order tracking, thermal test results, billing,
WaveKraft analytics — a Netlify-hosted app behind <https://www.temperpack.com/portal>) and a
**nopCommerce e-shop** at <https://store.temperpack.com/>. Neither exposes a documented developer
interface; the store answers HTTP 200 with its login page for every path, which produces false
positives on naive spec probes.

## What is here

| Path | What it is |
|---|---|
| `apis.yml` | APIs.json 0.20 index — company identity and website properties |
| `llms/temperpack-llms.txt` | TemperPack's own `llms.txt`, fetched verbatim from https://www.temperpack.com/llms.txt (HTTP 200) |
| `well-known/temperpack-well-known.yml` | Contract-discovery + `/.well-known/` probe record across every host |
| `security/temperpack-domain-security.yml` | Probed TLS / HSTS / DNSSEC / CAA / SPF / DMARC posture |

## Notes

- `status.temperpack.com` is CNAMEd to Freshstatus but **no status page is provisioned** — the app
  returns `Status page not found`, and HTTPS on the custom domain fails hostname validation
  (cert `CN=*.freshstatus.io`). No status page is claimed here.
- `github.com/TemperPack` is a real org (contact `it@temperpack.com`) but carries only four forks of
  third-party projects — no first-party code or specs.
- `saimjaved-sj/temperpack-uberfreight-sys-api` (RAML, May 2026) is an individual's repo, not a
  TemperPack publication, and is deliberately not registered here.
- The `temperpack.com` domain publishes SPF and DMARC, but DMARC policy is `p=none` and there is no
  DNSSEC and no CAA record.
