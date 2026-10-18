# Implementation roadmap and acceptance ledger

Status as of 2026-10-18: design prepared; all implementation and live acceptance below remain open. Governing owner scope is the request to restructure the startup website, independent project, MCP domains and future distribution. Pricing and paid launch have not been selected.

Work in coherent bundles of whole batch subsections. Do not fragment an extraction or a customer access flow into helper-sized PRs. Preserve independent implementation and acceptance status. Each subsection below has a bounded outcome and evidence requirements suitable for a lower-effort coding agent.

## Bundle A — truthful independent company website

### RAS-1: extraction and independent build

Input: `apps/marketing-robinson`, brand assets/styles, standalone architecture.

Deliver:
- New private company repository and dedicated Vercel project, linked to the intended account/team.
- Copy only necessary source/assets/configuration; retain source provenance.
- Replace external workspace dependencies, inherited tsconfig, root-dependent scripts, Vercel root install/build and turbo-ignore.
- Remove unused bundle analyzer setup or make it truly optional. Create a standalone lockfile.
- Remove Cortiware `/portal` rewrite from the new product. Retain only reviewed compatibility redirects for legacy links to the existing provider application.
- Add CI for isolated install, typecheck, lint, build and relevant route/browser checks.

Acceptance: fresh checkout installs and builds without the Cortiware checkout, Prisma generation, provider DB or provider credentials. Build creates every expected company route. Asset provenance and dependency inventory recorded. CI passes on the exact proposed revision.

### RAS-2: startup content and design preservation

Input: CONTENT.md and current rendered site/design references.

Deliver: revise home, about, why, services, products, industries, security, contact, footer, error pages and metadata/JSON-LD. Preserve actual logo artwork, tokens, gradients and responsive character. Replace generic enterprise claims and implied customer success with factual descriptions. Remove unused fake customer-logo assets. Route old page paths to their honest replacements rather than leaving stale claims accessible.

Acceptance: all routes and metadata audited; no Fortune 500 track record, unverified certifications, fabricated client logos, invented team or unsupported uptime/support promise. Every CTA resolves. Confirm email deliverability before relying on an existing alias; do not create assumed departments. Review desktop and mobile screenshots against original design. Security and privacy statements match implemented behavior. Legal review, if needed for paid launch, is tracked separately from completing this UI work.

### RAS-3: factual catalog and setup guides

Deliver: typed catalog, `/tools`, product detail pages, documented statuses, publication filtering, tested setup guides for offerings actually available. Present the Hub as optional. Product narratives distinguish tools from Cortiware business software. Keep pricing unannounced until chosen.

Acceptance: private records absent from every public output, including static bundles; unaccepted tools have no working public-connect invitation. Each published guide identifies the real tested connection URL and permissions. Keyboard/mobile navigation works; broken link checks pass. Product-status evidence references are recorded.

## Bundle B — website cutover and branded MCP addresses

### RAS-4: company-site cutover

Deliver: reviewed staging production build, configuration inventory, canonical domain migration, rollback record, website observation and source ownership documentation.

Acceptance: actual new domain-serving revision identified; HTTPS works on apex and www; redirect preserves path/query without a loop; images, routes, robots and sitemap work; contact route is usable; Cortiware provider/tenant bindings and intentional paused state are preserved. Old company website project retained until stabilization. Latest deployment READY alone is insufficient; inspect domain-serving behavior. Cortiware application availability is intentionally not a website-launch requirement while the owner has parked that product.

### RAS-5: first MCP domain migration

Choose a service whose deployed code is ready for meaningful authenticated acceptance. Do not wait for the entire suite to be publicly complete. Review its governing docs before changing origin/auth configuration.

Deliver: service-owned custom hostname, exact issuer/resource/callback migration, old-origin compatibility and client setup guide. Any service changes belong in that service repository; company repo records canonical public metadata and evidence.

Acceptance: real branded-origin MCP initialization, listing and an authorized operation; expected refusal with insufficient authority; OAuth callback/refresh/revocation when supported; old connection behavior verified; audience isolation retained; browser/mobile/client behavior accurately documented. Record reconnect requirements rather than masking them with redirects.

### RAS-6: remaining MCP domains and catalog reconciliation

Deliver: apply the proven migration pattern separately to each eligible MCP service and Hub. Mark unready migrations pending with their actual dependency. Do not duplicate execution/credentials into the company site.

Acceptance: per-service evidence ledger includes hostname, transport, deployed revision, authorization test, old-origin compatibility and known client limitations. Catalog availability agrees with service records. Existing owner sessions and optional Hub connections are exercised where authorized.

## Bundle C — customer access before monetization

### RAS-7: identity and product access backend

Deliver: independent customer identity, optional organizations/memberships, product-access records, invite/manual/free grant paths, audit trail and service-owned connection references. Choose auth based on verified service compatibility; do not reuse Cortiware auth as a shortcut.

Acceptance: account A cannot read/change B's data or connections, including guessed IDs; membership removal takes effect; revoked access cannot be replayed; sessions are host-only and protected from CSRF; logs contain no provider tokens; provider grants remain service-owned. Exercise two independently controlled principals before claiming multi-user acceptance. If a second real account is unavailable, complete implementation/testing and record real acceptance pending without blocking unrelated work.

### RAS-8: complete customer onboarding and owner access management

Deliver: functioning discover → access → provider authorize → AI-client connect → inspect/revoke flow; invite/access-management screen for owner; support request path with actual delivery/storage. Use existing service consent routes where available. Explain whether portal logout also revokes MCP/provider connections.

Acceptance: complete an invited/free customer journey on mobile and desktop clients actually supported; verify denial before entitlement and successful operation after grant when entitlement is required; revoke one connection without affecting another. No decorative dashboard, fake usage counters or no-op buttons. Record account deletion versus service disconnect behavior.

### RAS-9: service public-readiness and distribution

Deliver: per-service release assessment, public setup/support docs, product-specific access policy, resource/abuse controls appropriate to actual hosting, operational incident/rollback procedures, reviewed privacy disclosures. Public listing is a separate publication decision; prepare the artifacts before asking for a remaining decision.

Acceptance: each offered service passes its own live multi-user/client/permissions/revocation checks. Development-agent restrictions have not leaked into customer features. Private services remain undiscoverable. Every public capability and status has evidence. Website completion does not falsely mark service roadmap work complete.

## Bundle D — optional commercial launch

### RAS-10: monetization decision and implementation

Dependency: owner selects product/bundle packaging, prices or charge basis, provider-cost responsibility, refund/cancellation/grace policy and launch audience. Present a concrete comparison using known hosting/operations costs before asking. Continue other completion work while that decision is open.

Deliver after decision: server-controlled checkout, webhook processing and reconciliation, subscription/customer management, entitlement mapping and clear cost disclosures. Keep free/manual access supported where the chosen product model allows it.

Acceptance: duplicate/out-of-order webhook processing, unpaid/paid/cancelled states, expiry/grace, refunds and billing reconciliation tested in the processor's test environment. Confirm production payment setup and policies before taking a real charge. Do not treat a live checkout URL as proof of commercial readiness.

## Completion evidence format

Maintain one row per subsection and a separate row per MCP migration/public launch:

| ID | Implementation | CI/source revision | Deployment revision | Live acceptance | Evidence/blocker |
| --- | --- | --- | --- | --- | --- |
| RAS-1 through RAS-10 | Not started | — | — | Pending | This design is the starting point |

Use specific states and dates. Attach screenshots for design acceptance, redacted authenticated-test receipts for MCP acceptance, and exact revision links. Never include credentials, session cookies, personal provider data or token-bearing URLs.

## Next-agent bootstrap

Read this directory and the current repositories' governing instructions. Reconcile source, PRs, domain-serving production and existing provider services. Execute Bundle A first as one usable company-site outcome; retain all design tokens and actual logo assets. Prepare and verify migration before moving domains. Do eligible domain/service work without waiting for undecided billing. Report implemented and accepted separately, preserving every unfinished item with its concrete dependency.
