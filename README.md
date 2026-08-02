# TemperPack

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
