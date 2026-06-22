# CashKaro Product Catalog

Single source of truth for how we build products at CashKaro.

Every feature lives in `features/`. Every decision, spec, design requirement, test, and data analysis for a feature lives inside its folder — nothing external.

---

## Domains

| Domain | What it covers |
|--------|---------------|
| [Cashback](../domains/cashback/catalog-info.yaml) | Cashback tracking, wallet, payouts |
| [Discovery](../domains/discovery/catalog-info.yaml) | Search, store pages, coupons, deals |
| [Growth](../domains/growth/catalog-info.yaml) | Onboarding, referrals, SevaKaro |
| [Platform](../domains/platform/catalog-info.yaml) | Auth, notifications, settings |

---

## How to add a new feature

1. Create `features/your-feature-name/`
2. Copy structure from `features/sevakaro/`
3. Fill `catalog-info.yaml` — set `lifecycle: concept`
4. Fill `docs/index.md` with overview
5. Add path to root `catalog-info.yaml` targets
6. Open a PR with the PR template filled out
7. Get approval → merge → Roadie picks it up in ~60 seconds

## Lifecycle rules

| Stage | `lifecycle` value | What must be true |
|-------|------------------|-------------------|
| Idea | `concept` | index.md exists |
| Being specced | `concept` | PRD in progress |
| Ready to build | `in-development` | PRD complete, DRD complete, eng scoped |
| Live | `production` | Shipped to users |
| Retired | `deprecated` | No longer active |

## Reading this as an AI

Feed any feature's `docs/` folder to an AI for full context. The folder structure is always:
- `index.md` — overview and status
- `prd.md` — what we're building and why
- `drd.md` — how it should look and behave
- `research.md` — what we learned before building
- `data-analysis.md` — metrics and instrumentation
- `decisions.md` — decisions made and why (immutable)
- `testing/` — test plan and results
