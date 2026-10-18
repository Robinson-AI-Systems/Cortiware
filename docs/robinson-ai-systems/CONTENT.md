# Startup positioning and content implementation brief

## Voice and design

Confident, direct, honest about the business's current stage. Explain useful workflows and what is being built. No invented customers, testimonials, partners, staff, certifications, revenue, ROI, SLA, market leadership or guaranteed business outcomes.

Retain the existing Robinson logo files after visual verification; emerald `#00B67A`, electric teal `#00E3C2`, charcoal `#0C0C0C`, graphite `#1E1E1E` and mist-white `#F8FAF8`; the existing typography family choices, rounded cards and gradient accents. Preserve mobile navigation and refine accessibility/contrast where necessary. Do not replace the visual identity with a generic template.

## Proposed homepage copy

Eyebrow: **Independent software startup**

Headline: **Practical software. More capable AI.**

Introduction: Robinson AI Systems is a startup developing software and tools that help AI assistants work with real business systems. Our focus is practical automation, useful connections, and keeping people in control of their accounts.

Primary action: **Explore our tools** → `/tools`

Secondary action: **About Robinson AI Systems** → `/about`

Section: **What we're building**

- **MCP tools:** Connections between compatible AI assistants and the services people already use. Each product page explains its capabilities, access requirements and current availability.
- **Robinson's Toolkit Hub:** An optional way to work with compatible tools through one connection. Individual tools can also be used directly.
- **Business software:** Products exploring practical business workflows, including Cortiware. Show each product's verified development or release status.

Section: **Built around your work**

Start with a real task. Connect the right accounts. Give your assistant the permissions you choose. Our goal is to make that workflow easier to understand and manage as these products develop.

Section: **Follow the progress**

We're building the foundations now. Explore product pages to see what is available, what is being tested and what is still in development.

Do not add a Subscribe/Get Updates form unless submissions are actually persisted and delivered through a working system. Use a verified contact path or product guide instead.

## Route-by-route audit

| Source | Current problem | Required replacement |
| --- | --- | --- |
| `/` | Enterprise-at-scale claims; sales-led positioning; no MCP catalog | Startup introduction, truthful product focus, links to tools/about |
| `/about` | Established delivery-partner language | Startup story, goals and verified current work; optional factual founder introduction |
| `/why` | Fortune 500 track record, world-class team, dedicated team | Working principles: practical tasks, explicit permissions, clear availability, direct or Hub access |
| `/services` | Broad consulting/training/delivery promises | Actual offerings only; describe work being explored without representing a staffed service organization |
| `/products` | Cortiware plus generic custom AI only | Verified software products plus MCP product directory; accurate availability |
| `/industries` | Cortiware-specific package implementation details on company site | High-level product use cases or redirect to appropriate product information; no implied customer industries served |
| `/security` | SOC 2/HIPAA-ready language, 24/7 monitoring/security-team promises | Factual permissions, service-owned credentials, revocation guidance and security contact only where verified |
| `/contact` and footer | Many assumed departmental email aliases | One verified contact route; existing aliases require delivery checks |
| `/privacy` | Employee training/audit/process claims not evidenced | Disclosures matching actual website, portal and service data practices; fixed revision date |
| `/terms` | Generic enterprise-consulting terms | Scope aligned to what is actually offered; revisit before inviting paying customers |
| `error.tsx` | Says team notified without evidence of notification | Tell the visitor an error occurred and offer a working retry/contact route |
| `layout.tsx`, route metadata, JSON-LD | Enterprise positioning persists outside visible page copy | Consistent startup descriptions; correct route-specific canonicals |
| `public/logos` | Fictional company assets could imply customers | Remove unused fictional marks; display real customer/partner marks only with a factual basis |

## Tool detail page

Every listed tool answers:

1. What does this help me do?
2. What stage is it at, and who can access it?
3. Which provider account/permissions do I need?
4. Which AI clients and device flows have actually been tested?
5. What is the exact connection/setup process?
6. How do I inspect permissions and disconnect/revoke access?
7. Are Robinson charges announced? What separate provider charges may apply?
8. Where do I get support and see known limitations?

Example positioning: **GitHub tools for AI assistants**. Describe only verified service capabilities; do not promise superiority to another connector or call it publicly available while release acceptance is unfinished.

## Copy acceptance

Audit visible copy, metadata, structured data, social images, alt text and old indexed routes. Inspect the rendered design at phone and desktop widths. Assertions such as certification or uptime require service-specific evidence, not a hosting vendor's certification. Factual security descriptions are not a substitute for testing the underlying controls.
