# Cortiware reversible hosting pause

Owner direction, 2026-10-18: Cortiware is back-burnered and does not currently need hosting. Preserve it for later resumption while proceeding with the independent Robinson AI Systems business website.

## Applied and verified

Team: `team_PUafLQmqT7LYBaBs8lEOPYMG`.

| Project | Project ID | Applied operation | HTTP verification |
| --- | --- | --- | --- |
| cortiware-marketing-cortiware | prj_O5Fakz26Drew0V5tycIbwJSAYSQL | Vercel pause project | Default production alias: 503, `x-vercel-error: DEPLOYMENT_PAUSED` |
| cortiware-tenant-app | prj_mUQKeWPH4KMkY2XzIrAYdRUFv43Q | Vercel pause project | Default production alias: 503, `x-vercel-error: DEPLOYMENT_PAUSED` |
| cortiware-provider-portal | prj_vtuMi117XwV51s1fBd2rthPo4yZI | Vercel pause project | Default production alias: 503, `x-vercel-error: DEPLOYMENT_PAUSED` |
| cortiware-marketing-robinson | prj_VwnpJrIFFZN5t8gpHPSoH70YNIbF | Excluded from pause | `https://www.robinsonaisystems.com`: HTTP 200 |

All three pause API calls succeeded. Verification was performed immediately afterward. This checks default production aliases; it is not an inventory or disabling of every historical preview deployment.

No project, domain, repository, database or configuration was deleted. Environment secrets and DNS/mail records were not changed. MCP hosting projects were excluded. No new payment, storage or database changes were made.

This is a production-traffic pause, not a guarantee of zero account spending. Database/storage retention, domain renewal, GitHub scheduled workflows, preview deployments and future builds have not been disabled by this work. Reconcile these separately before reporting a full cost shutdown. Preserve security checks while the repository still contains the active company website.

## Resume later

1. Obtain an owner instruction to resume Cortiware; company-site work alone does not imply resumption.
2. Reconcile repository main and each actual production deployment. The project API's latest deployments were ERROR before the pause, so unpausing is not proof that the software is healthy or current.
3. For each intended project, invoke Vercel `unpause_project` with the project ID above and the same team, or use the corresponding Vercel project resume control.
4. Verify production alias/domain routing, application health and only then the relevant login/data flows. Repair and stage a tested release if needed under the repository's deployment instructions.
5. Record the actual resumed revisions and test evidence. Preserve all existing data; do not reset or seed databases as part of resumption.

## Relationship to company-site extraction

The company website remains active in its existing project until independently built and migrated. Preserve old Cortiware provider-route ownership, but remove inappropriate new-site reliance on that paused portal. Present Cortiware accurately as a paused/in-development product if mentioned; do not direct visitors into its paused application as a working signup.
