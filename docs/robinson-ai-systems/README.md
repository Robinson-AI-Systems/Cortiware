# Robinson AI Systems: independent startup website and MCP distribution

Owner request: 2026-10-18. Status: architecture and implementation plan; no migration or public tool launch has occurred.

## Outcome

Preserve the current Robinson logo, emerald/teal palette, dark surfaces, typography, cards, gradients and responsive character. Replace established-enterprise positioning with an accurate account of a startup developing software and MCP tools. Give the business independent source, deployments and operations. Use its existing domain for stable MCP service addresses and a future customer entry point.

This directory is the handoff authority for this new work. It does not reopen Cortiware's unrelated backlog. Copy it into the independent repository at extraction and leave a link here.

- [Architecture and migration](ARCHITECTURE.md)
- [Ordered implementation and acceptance](ROADMAP.md)
- [Content brief and replacement copy](CONTENT.md)

## Verified starting point

Inspected 2026-10-18 against Cortiware main `49aca91169dbae1521b2edd4815220c7318bc36d`.

| Item | Actual state |
| --- | --- |
| Source repository | `Robinson-AI-Systems/Cortiware` |
| Website application | `apps/marketing-robinson` |
| Existing Vercel project | `cortiware-marketing-robinson` |
| Project ID | `prj_VwnpJrIFFZN5t8gpHPSoH70YNIbF` |
| Team ID | `team_PUafLQmqT7LYBaBs8lEOPYMG` |
| Registered website domains | `robinsonaisystems.com`, `www.robinsonaisystems.com`, both verified |
| Current canonical direction | Apex redirects to `www` |
| Latest deployment reported by project API | `dpl_GqJgV8JWRFJrt6Qg963KQSU8KDXj`, production target, ERROR |
| Current domain-serving deployment | Not yet independently resolved; latest ERROR is not proof the public site is down |
| Build coupling | App scripts invoke `../../node_modules`; Vercel installs/builds from repository root |
| Configuration coupling | `tsconfig.json` extends `../../packages/config/tsconfig.base.json`; app declares `@cortiware/themes` |
| Cross-product routing | `/provider` redirects and `/portal` rewrites reference Cortiware's provider portal |
| Public-site fetch | Search fetch could not access the domain; visual review remains pending |

The business already has a separate Vercel project. Full independence requires extracting the source and build; merely renaming the current Vercel project is insufficient.

## Decisions carried forward

1. Business is a startup with no established customer base; never invent customers, traction, revenue, team size or certifications.
2. Preserve branding and visual design. This is a positioning and platform restructuring effort.
3. Each MCP service remains independently usable. The Hub is optional.
4. Provider credentials, consent, tool execution and permissions remain service-owned.
5. Development-agent spending/production restrictions must not become permanent end-user product restrictions.
6. Prepare monetization architecture; pricing, billing activation and commercial promises remain undecided.
7. A marketing launch, branded-domain migration, private pilot, public listing and paid launch are distinct milestones.
8. Preserve Cortiware code, data, configuration and hostname ownership. Owner subsequently requested parking Cortiware: its three non-company Vercel projects were reversibly paused; do not resume them as a website-migration side effect. See [pause record](../CORTIWARE-PAUSE.md).

## Scope and completion

The implementation ledger must distinguish source implemented, CI verified, deployed, real-world accepted and publicly offered. No unchecked acceptance item becomes complete because a page, mockup or endpoint exists.

The first usable milestone is an independently built, accurately positioned company site with a truthful tools directory. Public multi-user availability follows service acceptance; it must never be implied by adding a Connect button.
