# Public Architecture Overview

This document explains WhaleLand Swap at a system-boundary level. It deliberately omits implementation code, database schema, internal endpoints, infrastructure identifiers and production configuration.

## High-Level System

```mermaid
flowchart LR
    subgraph User["User-controlled boundary"]
        Browser["Web / PWA client"]
        Wallet["External wallet"]
    end

    subgraph Edge["WhaleLand edge platform"]
        Pages["Cloudflare Pages"]
        API["Workers / Hono API"]
        Controls["Access control · rate policy · capability gates"]
    end

    subgraph Data["Managed data services"]
        D1["D1 relational state"]
        KV["KV cache / state"]
        R2["R2 reserved / optional · currently disabled"]
    end

    subgraph External["External systems"]
        RPC["Blockchain RPC"]
        Market["Market data Providers"]
        DEX["DEX / route Providers"]
        Risk["Security Providers"]
        Services["Other approved services"]
    end

    Browser --> Pages --> API --> Controls
    Controls --> D1
    Controls --> KV
    Controls -.->|"reserved · disabled"| R2
    Controls --> RPC
    Controls --> Market
    Controls --> DEX
    Controls --> Risk
    Controls --> Services
    Wallet -->|"user approval"| Browser
    Browser -->|"wallet request / signed payload"| RPC
```

## Responsibility Boundaries

| Layer | Public responsibility description |
| --- | --- |
| Client | Product UI, input validation, state presentation and wallet-request initiation |
| Wallet | Private-key custody, user approval and signature creation under the wallet's own controls |
| Pages | Static delivery and edge entry point |
| Workers / Hono | API composition, policy enforcement, Provider orchestration and truthful error states |
| D1 / KV | Managed application data and caching in the active production configuration |
| Cloudflare R2 | Reserved / optional object storage capability; currently disabled in the active production configuration |
| Providers | Chain access, market data, routes, security signals and approved external services |

## Capability-Gated Requests

```mermaid
flowchart TD
    Request["Client request"] --> Registry["Resolve network"]
    Registry --> Capability["Check capability state"]
    Capability -->|"not enabled / not configured"| Closed["Unavailable or fail-closed response"]
    Capability -->|"eligible"| Provider["Call selected Provider"]
    Provider -->|"reachable with data"| Result["Normalized result"]
    Provider -->|"timeout / empty / error"| Degraded["Delayed, stale or unavailable state"]
    Result --> Client["Client presentation"]
    Degraded --> Client
```

The platform does not treat network registration or adapter presence as proof that a live capability is ready. Implementation, configuration, reachability and data availability are evaluated separately.

## External-Wallet Transaction Boundary

1. The application prepares or requests a route based on the selected network and current Provider state.
2. The client presents the intended action to the user.
3. For an external-wallet path, the user's wallet performs its own approval and signing flow.
4. Submission and receipt state are tracked separately from UI intent.
5. Missing receipts, rejected signatures or unavailable Providers must not be represented as completed execution.

Separately gated signing and operational services can have different trust and authorization boundaries. Their implementation and controls are intentionally outside this public showcase.

## Intentionally Omitted

- Worker and Hono implementation
- Chain execution and wallet-signing implementation
- Swap, AMM, Launch and settlement algorithms
- Internal Admin architecture details
- Database tables, migrations and seed data
- Provider endpoints and production account identifiers
- Credentials, secret names and secret values
- Deployment commands and runnable infrastructure configuration
