# CashKaro Product Catalog

One place for everything product. Every feature we build lives here — its spec, design requirements, research, data analysis, decisions, and test results. Nothing lives in someone's head, a random Notion page, or a Slack message.

---

## Why this exists

- **New joiner?** Read any feature folder and you know exactly what was built, why, and what decisions were made.
- **PM working on a feature?** Everything is in one folder. No hunting across Confluence, Figma, and Slack.
- **Engineer starting work?** Read the PRD + DRD + decisions before writing a line of code.
- **AI assistant?** Feed it any `docs/` folder and it has full context to help you build.
- **Stakeholder review?** Every change goes through a PR — nothing changes without a review.

---

## Folder structure

```
product-catalog/
├── features/              ← one folder per feature, everything inside
│   └── sevakaro/
│       ├── catalog-info.yaml    ← feature metadata (status, owner, links)
│       ├── mkdocs.yml           ← doc navigation
│       └── docs/
│           ├── index.md         ← overview and current status
│           ├── prd.md           ← product requirements
│           ├── drd.md           ← design requirements
│           ├── research.md      ← user and market research
│           ├── data-analysis.md ← metrics and instrumentation
│           ├── decisions.md     ← decisions made and why (permanent record)
│           └── testing/
│               ├── test-plan.md
│               └── test-results.md
├── domains/               ← product areas (cashback, discovery, growth, platform)
├── org/                   ← teams and members
└── docs/                  ← how we work as a product team
```

---

## Rules

**1. Every feature change goes through a PR.**
No direct pushes to `main`. Open a pull request, fill the PR template, get it reviewed. This is enforced via branch protection.

**2. The feature owner must approve spec changes.**
CODEOWNERS ensures the right person reviews the right folder. Engineering must approve before lifecycle moves to `in-development`.

**3. Decisions are permanent.**
Never edit a past ADR in `decisions.md`. If a decision changes, add a new ADR that supersedes the old one. This gives us a clear history of why things changed.

**4. Lifecycle must reflect reality.**
The `lifecycle` field in `catalog-info.yaml` must always match where the feature actually is. Don't leave it as `concept` when it's live.

| Value | Meaning |
|-------|---------|
| `concept` | Idea or draft spec |
| `in-development` | PRD done, engineering building |
| `production` | Live to users |
| `deprecated` | No longer active |

**5. Every document in a feature folder must be filled before moving to `in-development`.**
- PRD: problem, user stories, success metrics, scope ✓
- DRD: screens, component specs, Figma link ✓
- No open questions blocking start ✓

---

## How to add a new feature

**Step 1 — Create the folder**
```
features/
└── your-feature-name/
    ├── catalog-info.yaml
    ├── mkdocs.yml
    └── docs/
        ├── index.md
        ├── prd.md
        ├── drd.md
        ├── research.md
        ├── data-analysis.md
        ├── decisions.md
        └── testing/
            ├── test-plan.md
            └── test-results.md
```

Copy the `sevakaro` folder and rename it. Replace all content with your feature's details.

**Step 2 — Add a Port entity file**
```
.port/entities/features/your-feature-name.json
```
Copy `.port/entities/features/sevakaro.json`, update the `identifier`, `title`, `description`, `tags`, and `relations`.

**Step 3 — Register in the root catalog**
Open `catalog-info.yaml` at the repo root and add your feature path to the `targets` list:
```yaml
- ./features/your-feature-name/catalog-info.yaml
```

**Step 4 — Open a PR**
Fill the PR template. Get it reviewed. Merge. Port picks it up within minutes.

---

## What is Port and how we use it

**Port (getport.io)** is our product portal — a visual UI that reads from this GitHub repo and displays all our features in one place. Think of it as the frontend for this repo.

Every time you merge a change to `main`, Port automatically syncs and the UI updates.

### What Port shows us

| Feature | What it does |
|---------|-------------|
| **Catalog** | Every feature card with status, owner, domain, and links to Figma and Confluence |
| **Blueprints** | The schema that defines what a "Feature" or "Domain" looks like |
| **Relations** | Which feature belongs to which domain — visualised as a graph |
| **Scorecards** | Rules that check if a feature is fully defined (has PRD, has Figma link, has metrics, etc.) |
| **Lifecycle tracking** | Filter features by stage — concept, in-development, production |

### Port vs just using GitHub

GitHub shows you files. Port shows you the catalog as a product — filterable, searchable, with status indicators, scorecards, and relationship graphs. It's what you show stakeholders, new joiners, and the broader team. GitHub is where you edit.

### Our Port setup

- **Blueprint: Domain** — product areas (Cashback, Discovery, Growth, Platform)
- **Blueprint: Feature** — each product feature with lifecycle, owner, Figma, Confluence
- **Relation** — Feature belongs to a Domain
- **Entities** live in `.port/entities/` in this repo
- **GitHub integration** scans `.port/entities/**/*.json` on every push

---

## Benefits

- **Single source of truth** — one repo, one place, no duplication
- **AI-ready** — feed any `docs/` folder to Claude or any AI for full feature context
- **Review-enforced** — GitHub PRs and CODEOWNERS mean nothing changes without sign-off
- **Always up to date** — Port syncs on every merge, stakeholders always see the latest state
- **Onboarding in minutes** — new joiners read the repo, not 6 different tools
- **Decision history** — `decisions.md` in every feature is a permanent record of why things are the way they are
