# Caelara Labs API benchmarks

Daily latency measurements for the ten Caelara Labs API suites (`*.caelaralabs.com`).

Last run: **2026-11-21T00:58:47.416Z** · Live JSON: https://benchmarks.caelaralabs.com/api/v1/benchmarks

| Suite | Endpoint | p50 | p95 | min | successful calls | Price per 1,000 calls (USD) | Badge |
|---|---|---|---|---|---|---|---|
| Web Intelligence (`api`) | `/v1/prompt-firewall-structurer` | 12.0 ms | 15.0 ms | 11.0 ms | 10/10 | $5.00 | ![api](https://benchmarks.caelaralabs.com/badge/api.svg) |
| Social Analytics (`social`) | `/v1/engagement-rate-calc` | 12.0 ms | 14.0 ms | 11.0 ms | 10/10 | $5.00 | ![social](https://benchmarks.caelaralabs.com/badge/social.svg) |
| Agent Safety (`agent`) | `/v1/pii-redactor` | 11.0 ms | 15.0 ms | 11.0 ms | 10/10 | $5.00 | ![agent](https://benchmarks.caelaralabs.com/badge/agent.svg) |
| Compliance & Trust (`compliance`) | `/v1/iban-bic-validator` | 12.0 ms | 16.0 ms | 12.0 ms | 10/10 | $5.00 | ![compliance](https://benchmarks.caelaralabs.com/badge/compliance.svg) |
| E-Commerce Intelligence (`ecom`) | `/v1/gtin-upc-validator` | 11.0 ms | 15.0 ms | 11.0 ms | 10/10 | $5.00 | ![ecom](https://benchmarks.caelaralabs.com/badge/ecom.svg) |
| SEO & GEO Readiness (`seo`) | `/v1/serp-pixel-preview` | 13.0 ms | 15.0 ms | 12.0 ms | 10/10 | $5.00 | ![seo](https://benchmarks.caelaralabs.com/badge/seo.svg) |
| Document Utilities (`docs`) | `/v1/phone-e164-formatter` | 10.0 ms | 14.0 ms | 9.0 ms | 10/10 | $5.00 | ![docs](https://benchmarks.caelaralabs.com/badge/docs.svg) |
| On-Chain Intelligence (`crypto`) | `/v1/address-checksum-validator` | 12.0 ms | 14.0 ms | 10.0 ms | 10/10 | $5.00 | ![crypto](https://benchmarks.caelaralabs.com/badge/crypto.svg) |
| Global Locale (`geo`) | `/v1/distance-haversine-calc` | 12.0 ms | 14.0 ms | 10.0 ms | 10/10 | $5.00 | ![geo](https://benchmarks.caelaralabs.com/badge/geo.svg) |
| Dynamic Media (`media`) | `/v1/aspect-ratio-calc` | 12.0 ms | 42.0 ms | 11.0 ms | 10/10 | $5.00 | ![media](https://benchmarks.caelaralabs.com/badge/media.svg) |

## Method

- Per suite: 1 unmeasured warm-up call, then 10 sequential calls timed from request start to the last byte of the response body. Each call has a 5000 ms timeout. Only HTTP 200 responses count as samples. Percentiles are nearest-rank.
- Where it is measured from: A Cloudflare Worker (caelara-benchmarks) calling the public suite hostnames over HTTPS. Measured inside Cloudflare's network, so the numbers exclude the last-mile network between a client and Cloudflare and are not end-user latency.
- Each suite is measured on one pure-compute endpoint, so the numbers describe the Caelara edge and payment gate, not third-party data sources.
- The runner is scheduled daily at 06:00 UTC. Results are also stored at the JSON endpoint above.
- Prices are the published per-call list prices (0.005 USDC for atomic endpoints, 0.025 USDC for composite endpoints), shown per 1,000 calls.
- Comparisons with other providers appear only when a published, cited figure is available for that suite. None are listed today.

## Reproduce

Every endpoint above is public. With your own key (a free trial key: https://caelaralabs.com/shield/#trial):

```bash
curl -s -o /dev/null -w "%{time_total}\n" -H "X-Caelara-Key: $KEY" "https://geo.caelaralabs.com/v1/distance-haversine-calc?lat1=0&lon1=0&lat2=1&lon2=1"
```

Contact: ops@caelaralabs.com
