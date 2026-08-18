# Developer Platform Overview

WhaleLand's API platform connects product, data, execution-state, and operational domains behind capability and access-control boundaries. This document is a public capability summary, not an API specification. It contains no implementation, internal route list, authentication material, or runnable examples.

## Developer Capability Domains

| Domain group | Included capabilities |
| --- | --- |
| Market & Token Data | Discovery, metadata, prices, history, holders, news, watchlists, and normalized data states |
| Multi-chain Data | Chain registry, capability resolution, chain state, bridge status, and cross-network discovery |
| DEX Quotes & Routing | Quote aggregation, route preparation, orders, and separate preparation, submission, and receipt states |
| Pools & Liquidity | Pool discovery, liquidity state, and network-specific availability |
| Launch | Token launch, project lifecycle, and launch-task state |
| Contract Risk | Provider-backed token and contract signals with explicit unavailable or degraded outcomes |
| Wallet & Execution State | Wallet integration boundaries, transaction preparation, chain execution state, and receipts |
| AI-assisted Interfaces | Search, query, guidance, market intelligence, and preparation-oriented workflows |
| Platform & Account | Identity, profile, access control, sessions, notifications, content, and benefits |
| Analytics & Operations | Product analytics, integrations, status, content operations, and separated Admin boundaries |

Public availability, authentication, access policy, and versioning are separate concerns for every product surface.

## Engineering Inventory Snapshot

| Metric | Count |
| --- | ---: |
| Internal API handlers | **500+** |
| API modules | **40+** |

These values come from current static inspection and are deliberately rounded. They measure internal engineering scope; they do **not** mean that 500+ APIs are publicly available, documented, or covered by a stable public contract.

## Platform Design Principles

- Network and capability checks precede Provider-dependent operations.
- Read, preparation, submission, and receipt states are not conflated.
- Public data, authenticated products, and operator-only surfaces have separate access boundaries.
- Provider errors are normalized into explicit unavailable, delayed, stale, or degraded states.
- AI-assisted interfaces provide data, preparation, and tracking boundaries rather than autonomous signing or trading.
- Sensitive configuration is supplied by the managed runtime, not repository content.
- Admin and user-facing permissions remain separate.

## Public Disclosure Boundary

This overview intentionally excludes:

- Complete route paths and request or response schemas
- Worker and Hono handlers
- Provider endpoints, credentials, and infrastructure identifiers
- Database schemas, migrations, and seed data
- Wallet-signing and chain-execution implementation
- Trading, launch, settlement, rebate, allocation, or pricing logic
- Internal Admin mutations and operational controls
- Rate-policy values, customer plans, and billing rules

For the network readiness model, see [CAPABILITIES.md](./CAPABILITIES.md). For system and security boundaries, see [ARCHITECTURE.md](./ARCHITECTURE.md) and [SECURITY.md](./SECURITY.md).
