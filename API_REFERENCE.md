# API Reference

> **Status: Under active development.** This describes the CeloHT API's intended design and currently published endpoint set. As the platform evolves, additional endpoints will be documented here — verify against the live API's `/health` response before integrating anything mission-critical.

## Overview

The CeloHT API lets developers integrate with community services, educational resources, impact data, and CeloHT's blockchain-powered tools.

## Design Principles

- RESTful architecture
- JSON responses
- HTTPS only
- Secure, token-based authentication
- Versioned endpoints (`/v1/`, `/v2/`, ...)
- Documentation kept in the open, alongside the code

## Base URLs

```
Production:  https://api.celoht.org/v1
Development: https://dev-api.celoht.org/v1
```

## Authentication

Protected endpoints require a bearer token:

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Response Format

**Success:**
```json
{
  "success": true,
  "data": {}
}
```

**Error:**
```json
{
  "success": false,
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

## Public Endpoints

| Endpoint | Description |
|---|---|
| `GET /health` | Health check — returns `{ "status": "ok", "version": "1.0.0" }` |
| `GET /programs` | All active CeloHT programs |
| `GET /education/courses` | Available educational courses |
| `GET /agents` | Verified community agents (cross-references on-chain verification where applicable — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)) |
| `GET /reforestation` | Active environmental initiatives |
| `GET /impact` | Ecosystem impact metrics — see [METRICS.md](./METRICS.md) for methodology |
| `GET /partners` | Official partners — see [PARTNERS.md](./PARTNERS.md) |
| `GET /news` | Latest announcements |

## Protected Endpoints

Authentication required for all of these:

```
POST /agents/register
POST /education/certificates
POST /governance/proposals
POST /governance/vote
```

## Rate Limits

- 100 requests per minute (default)
- Burst protection enabled
- Higher limits available for approved partners on request — see [PARTNERS.md](./PARTNERS.md)

## HTTP Status Codes

| Code | Meaning |
|---|---|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 429 | Too Many Requests |
| 500 | Internal Server Error |

## Versioning

Semantic versioning at the URL path level (`/v1/`, `/v2/`). Breaking changes only ship in a new major version — see [RELEASE_MANAGEMENT.md](./RELEASE_MANAGEMENT.md).

## Security

All API traffic uses HTTPS/TLS. Beyond transport encryption: authentication tokens, rate limiting, request validation, input sanitization, and logging/monitoring. See [SECURITY.md](./SECURITY.md) and [THREAT_MODEL.md](./THREAT_MODEL.md).

## SDK Support

Planned SDKs: JavaScript, TypeScript, Python, Go, Dart, Rust. See [SDK.md](./SDK.md) and [CLI.md](./CLI.md) for what's specified so far.

## Example

```bash
curl https://api.celoht.org/v1/programs
```

```json
{
  "success": true,
  "data": [
    { "id": "education", "name": "Financial Education" },
    { "id": "agents", "name": "Agent Network" },
    { "id": "reforestation", "name": "Reforestation" }
  ]
}
```

## Changelog

API changes are tracked in [CHANGELOG.md](./CHANGELOG.md).

## Support

Bug or question about the API? Open a GitHub issue, start a GitHub Discussion, or contact the maintainers — see [SUPPORT.md](./SUPPORT.md) and [CONTACT.md](./CONTACT.md).

## License

The CeloHT API is part of the CeloHT open-source ecosystem, licensed under Apache 2.0 — see [LICENSE](./LICENSE).

## References

- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [SDK.md](./SDK.md)
- [METRICS.md](./METRICS.md)
