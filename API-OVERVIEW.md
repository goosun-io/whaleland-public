# API Platform Overview

This is a scale and domain summary only. It is not an API specification and contains no implementation, internal endpoint list, authentication material or runnable examples.

## Engineering Inventory Snapshot

| Metric | Count |
| --- | ---: |
| Endpoint inventory | **513** |
| Business / platform domains | **34** |
| API source files | **43** |

The counts describe an engineering inventory snapshot and may evolve. Public API availability, access policy and versioning are separate concerns.

## Domain Summary

1. Account & Profile
2. Authentication & Session
3. Wallet Integration
4. Orders
5. Watchlist
6. Market Data
7. Token Data
8. Contract Risk
9. DEX Routing & Quotes
10. Pools & Liquidity
11. Launchpad
12. Launch Tasks
13. Chain Registry
14. Chain Execution
15. Bridge & Cross-chain Status
16. Discover
17. Community
18. Benefits
19. Tasks & Rewards
20. News
21. Notifications
22. Banners & Content
23. Analytics
24. Media Proxy
25. Integrations
26. AI Agent API
27. AI Assistant
28. API Gateway & Billing
29. Bot / Quant Billing
30. Admin Core
31. Admin Accounts
32. Admin Operations & Content
33. Admin Security & Analytics
34. Domain & Platform Status

## API Design Principles

- Capability and network checks happen before Provider-dependent operations.
- Read, preparation, submission and receipt states are not conflated.
- Access-controlled products are separated from public data surfaces.
- Provider errors are normalized into explicit unavailable or degraded states.
- Sensitive configuration is supplied by the managed runtime, not repository content.
- Admin and user-facing boundaries are separated.

## Not Included

- Complete route paths or request/response schemas
- Worker / Hono handlers
- Business rules, settlement or rebate logic
- Wallet-signing and chain-execution logic
- Internal Admin mutations
- Rate-policy values or customer plan details
- Provider endpoints, credentials or infrastructure identifiers
- Database schemas, migrations or seed data
