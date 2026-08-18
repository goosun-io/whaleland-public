# Security & Disclosure Boundary

This file documents the public security posture at a conceptual level. It does not claim that any system is absolutely secure.

## External-Wallet Boundary

- Users retain control of private keys through their wallet software in external-wallet flows.
- WhaleLand interfaces can initiate external-wallet requests but do not replace the wallet's approval screen.
- External-wallet trading actions require explicit user authorization.
- A prepared transaction is not represented as executed until the relevant result is available.

Separately gated signing or operational services have distinct authorization boundaries and are not documented in this public showcase.

## Platform Boundaries

- User, wallet, API, Provider and Admin permissions are treated as separate trust zones.
- Administrative capabilities use a separate control surface and dedicated access controls.
- Public, authenticated and operator-only API roles are distinct.
- Provider-dependent states can be unavailable, delayed, stale or unconfigured.
- Missing evidence must not be replaced with fabricated prices, receipts or transaction identifiers.

## Repository Hygiene

This public showcase intentionally excludes:

- Environment files and runtime configuration
- Credentials, keys, passwords and signing material
- Cloud account, database, cache and object-storage identifiers
- Private Provider endpoints and webhook configuration
- Production database schema, migrations and seed data
- Wallet implementation, chain execution and core trading code
- Internal incidents, debug dumps, account information and commercial reports

## Scope of This Showcase

The package contains Markdown documentation and selected product screenshots only. It has no package manifest, source tree, deployment workflow, schema or runtime configuration and cannot be used to deploy the commercial product.

## Responsible Contact

For a legitimate security or technical enquiry, use the current [goosun-io GitHub profile](https://github.com/goosun-io). Do not include credentials, private keys, recovery phrases or live exploit details in a public issue.
