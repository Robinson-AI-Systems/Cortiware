# Architecture and migration

## Ownership and repositories

Target: new private repository `Robinson-AI-Systems/robinson-ai-systems`, with a dedicated Vercel project of the same name. These are proposed resource names, not resources already created. The existing Cortiware source repository is public; do not copy its entire history, secrets, databases or unrelated application code into the new repository.

Extract the company website's assets, components and styles. Retain source attribution in a migration record containing the source commit and file inventory. Copy any needed shared configuration into the new repository. Remove `file:../../` dependencies and scripts reaching outside the repository. Use a standalone lockfile and `npm ci`; select supported dependency versions after checking current official releases and security advisories at implementation time.

Suggested initial layout:

```text
src/app/             Company pages, tools directory and connection guides
src/components/      Existing branded navigation, footer and visual primitives
src/content/         Typed product records and factual content
src/styles/          Robinson brand tokens and existing global styles
public/              Verified Robinson logos and favicons
docs/                Roadmap, acceptance ledger and operating runbooks
tests/               Navigation, catalog, accessibility and security checks
```

Keep the initial site independent of a database. Introduce the account backend only in the customer-access milestone. Do not introduce an empty dashboard or broken sign-in flow to suggest that the portal exists.

## Domain structure

Use the domain already owned. Hostnames below are proposed assignments and require collision checks against actual DNS and Vercel project-domain ownership.

| Address | Responsibility | Hosting owner |
| --- | --- | --- |
| `www.robinsonaisystems.com` | Company website, product catalog, setup guides | New company website project |
| `robinsonaisystems.com` | Redirect to canonical website | New company website project |
| `app.robinsonaisystems.com` | Future customer accounts and access management | Customer portal project when implemented |
| `github.robinsonaisystems.com` | GitHub MCP's existing transport and OAuth routes | Existing GitHub MCP project |
| `workspace.robinsonaisystems.com` | Google Workspace MCP | Existing Workspace MCP project |
| `stripe.robinsonaisystems.com` | Stripe MCP | Existing Stripe MCP project |
| `vercel.robinsonaisystems.com` | Vercel MCP | Existing Vercel MCP project |
| `neon.robinsonaisystems.com` | Neon MCP | Existing Neon MCP project |
| `hub.robinsonaisystems.com` | Optional universal Hub | Existing Hub project |
| `provider.robinsonaisystems.com` | Existing Cortiware administration | Existing Cortiware provider project |

Catalog pages use `/tools` and `/tools/[slug]` on the company website. Tool transport paths must be discovered from each service; do not assume `/mcp` is universal or route tool traffic through the marketing app.

Explicit subdomains allow each service to retain deployments, permissions, availability and logs. A company-site outage should not stop a user's connected MCP service. Do not install a wildcard proxy as a shortcut.

## Tool catalog contract

Start with reviewed records in `src/content/tools.ts`. Required fields:

```typescript
type ToolPublication = 'private' | 'listed' | 'public';
type ToolAvailability = 'development' | 'private-pilot' | 'public-beta' | 'available' | 'paused';
type CommercialAccess = 'unannounced' | 'free' | 'paid' | 'custom';
interface ToolProduct {
  id: string;
  slug: string;
  name: string;
  summary: string;
  publication: ToolPublication;
  availability: ToolAvailability;
  commercialAccess: CommercialAccess;
  audiences: string[];
  capabilities: string[];
  limitations: string[];
  setupGuidePath: string;
  connectionUrl: string | null;
  authorizationUrl: string | null;
  supportPath: string;
  lastVerifiedAt: string | null;
  evidenceRef: string | null;
}
```

Private records must be absent from public pages, static parameters, sitemaps, structured data, APIs and client bundles. A development tool may be publicly described only when explicitly marked listed. Availability and publication are independent; being deployed does not authorize public promotion. Default all imported records to private/development/unannounced until verified.

Show Connect only when the publication permits it, the service is accepted for the indicated audience, and a validated connection URL exists. Otherwise show a factual development/pilot label. Do not invent supported client integrations; verify ChatGPT, Claude, desktop and mobile independently where offered.

The catalog is descriptive. It must not become a second dispatcher, permission engine, provider token store or Hub replacement. RTC remains the compatibility contract for optional Hub connections.

## Customer access

Target experience: discover a tool, read availability/permissions/cost information, sign in if required, obtain access, connect their own provider account, connect their AI client, inspect and revoke access.

Website authentication does not authorize provider operations. Customer identity, product entitlement, MCP connection authorization and provider OAuth are separate records and checks. Reuse existing service onboarding when it is already customer-capable; do not add a mandatory central account for free direct connections without a concrete product need.

For a portal, use an independent identity system and host-only secure session cookies. Never reuse Cortiware provider, developer, accountant or tenant cookies. A customer may own an individual account or belong to an organization. Enforce organization membership on every scoped operation; UI filtering is insufficient.

Portal owns customer/product access records and billing references. Service owns provider tokens, tool grants, execution policy and audit results. Portal stores opaque service connection references and safe summaries only. Cross-service changes require audience-bound, short-lived, replay-resistant authorization and service-side membership validation. Never accept a browser-provided organization ID or paid flag as authority.

Suggested backend records for the portal milestone:

| Record | Purpose and constraints |
| --- | --- |
| Account | Stable internal principal; verified identity links; no email-only identity merges |
| Organization / Membership | Account role and organization ownership; explicit invitations and revocation |
| ProductAccess | Product, subject, source, state and expiry; invite/manual/free/subscription sources |
| ServiceConnectionRef | Subject, product and opaque service-owned ID; no provider credentials |
| BillingCustomerRef | Processor identity per subject; no card data |
| BillingEvent | Unique external event ID, processing state and audit timestamps |
| AccessAuditEvent | Actor, subject, action and safe metadata; retention policy explicit |

Access must work with manual/invite/free grants before billing exists. Service validation checks entitlement only for products whose published access model requires it. Removing a central paid entitlement must not erase provider data or silently revoke unrelated tools. Service connection revocation and portal logout must report their actual, distinct effects.

## Monetization preparation

Support optional product-specific subscriptions, bundles and manually granted access in the model. Do not choose prices, trial periods, billable units or automatic charges. Owner approval of a commercial model precedes checkout activation.

Future billing requirements: server-selected price IDs, signed and deduplicated webhooks, explicit product mapping, durable processing, out-of-order event handling, reconciliation, visible payment failure state, cancellation behavior and a defined grace policy. Provider charges and Robinson charges must be explained separately. Chargeable actions require the actual customer's applicable consent and service policies.

Do not copy the development agent's zero-spend or test-only rules into customer product access. Conversely, opening customer functionality does not waive the development agent's own execution constraints.

## Migration sequence

1. Inventory the actual domain-serving deployment, project settings, DNS, aliases, env names and public routes. Read Cortiware's go-live runbook before changing settings. Export configuration metadata without secret values.
2. Build the extracted site without Cortiware dependencies or credentials. Verify logos and all pages against the existing design visually on desktop and mobile.
3. Stage the new site's production build without moving the domain. Verify routing, canonical URLs, headers, redirects, forms or email links, sitemap, error pages and asset loading.
4. Record domain ownership moves and rollback steps. Move website domains only after the staged release passes. Do not change nameservers or email MX/TXT records as part of an application move.
5. Read back domain bindings and TLS; test apex-to-www behavior and all existing public paths. Check `provider.robinsonaisystems.com` still resolves to Cortiware. Keep the old website project available for rollback until stabilization is accepted.
6. Migrate MCP hostnames individually in their service repositories. Complete one service before repeating across others; website migration does not require all tools to migrate at once.
7. Retire only the old marketing application after confirming no remaining consumer/build dependency. Update Cortiware docs to link to the independent company repository. Never remove provider/tenant apps or their database resources.

## MCP origin migration checklist

For each service, record its current transport, discovery, OAuth issuer, resource identifiers, callback URLs, audience checks, cookies, public-origin variables, webhook destinations and connected-client requirements. A DNS alias alone is insufficient.

Add the branded hostname and provider-authorized callbacks first; test TLS, MCP initialization, tool listing, execution, OAuth consent/callback, refresh and revocation on that hostname. Preserve old origins while required by existing sessions. Never redirect a credential-bearing MCP POST across origins as a migration shortcut. Do not loosen audience/issuer validation to accept arbitrary hosts.

An origin/issuer change may require a client's reconnection. State any unavoidable reconnection clearly; do not promise automatic discovery refresh in clients the server does not control. Preserve tokens only where the existing security contract permits it. Publish the branded URL after authenticated acceptance, then plan legacy-origin retirement with compatibility evidence and a rollback path.

## Release boundaries

Website publication can precede public tool access. Tool public launch additionally requires its service's multi-user isolation, provider authorization, revocation, abuse handling, operating documentation and compatibility acceptance. A catalog should describe verified facts without claiming certification, guaranteed uptime or monitoring that has not been established.
