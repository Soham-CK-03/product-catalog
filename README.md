# CashKaro Product Catalog

One place for everything product. Every feature we build lives here — its spec, design requirements, research, data analysis, decisions, and test results. Nothing lives in someone's head, a random Notion page, or a Slack message.

---

## Why this exists

| Who | Benefit |
|-----|---------|
| **New joiner** | Read any feature folder and know exactly what was built, why, and what decisions were made |
| **PM** | Everything for your feature is in one folder — no hunting across Confluence, Figma, and Slack |
| **Engineer** | Read PRD + DRD + decisions before writing a line of code |
| **AI assistant** | Feed any `docs/` folder to Claude and it has full context to help you build |
| **Stakeholder** | Every change goes through a PR — nothing changes without a review |

---

## Folder structure

```
product-catalog/
├── features/                        ← one folder per feature, everything inside
│   └── sevakaro/
│       ├── catalog-info.yaml        ← feature metadata (status, owner, links)
│       ├── mkdocs.yml               ← doc navigation
│       └── docs/
│           ├── index.md             ← overview and current status
│           ├── prd.md               ← product requirements
│           ├── drd.md               ← design requirements
│           ├── research.md          ← user and market research
│           ├── data-analysis.md     ← metrics and instrumentation plan
│           ├── decisions.md         ← decisions made and why (permanent record)
│           └── testing/
│               ├── test-plan.md
│               └── test-results.md
├── domains/                         ← product areas (cashback, discovery, growth, platform)
├── org/                             ← teams and members
├── docs/                            ← how we work as a product team
└── .port/                           ← Port entity definitions (synced to UI automatically)
    ├── blueprints/                  ← schemas for Domain and Feature
    └── entities/                    ← one JSON file per entity
```

---

## Rules

**1. Every feature change goes through a PR.**
No direct pushes to `main`. Open a pull request, fill the PR template, get it reviewed. Enforced via branch protection + CODEOWNERS.

**2. The feature owner must approve spec changes.**
CODEOWNERS maps each feature folder to its PM. Engineering must approve before lifecycle moves to `in-development`.

**3. Decisions are permanent.**
Never edit a past ADR in `decisions.md`. If a decision changes, add a new ADR that supersedes the old one. This gives us a clear history of why things changed.

**4. Lifecycle must reflect reality.**
The `lifecycle` field in `catalog-info.yaml` and `.port/entities/` must always match where the feature actually is.

| Value | Meaning |
|-------|---------|
| `concept` | Idea or draft spec in progress |
| `in-development` | PRD done, engineering actively building |
| `production` | Live to users |
| `deprecated` | No longer active |

**5. A feature is not ready to build until all of these are filled:**
- [ ] PRD: problem statement, user stories, success metrics, scope
- [ ] DRD: screens defined, Figma link added
- [ ] No open questions blocking start
- [ ] Engineering has read and acknowledged the spec

---

## How to add a new feature

**Step 1 — Copy the sevakaro folder**
```
features/your-feature-name/
```
Rename all contents. Replace all text with your feature's details.

**Step 2 — Add a Port entity file**

Create `.port/entities/features/your-feature-name.json`:
```json
{
  "identifier": "your-feature-name",
  "title": "Your Feature Title",
  "blueprint": "feature",
  "properties": {
    "lifecycle": "concept",
    "description": "One line description",
    "figmaLink": "https://figma.com/your-link",
    "confluenceLink": "https://cashkaro.atlassian.net/your-link",
    "tags": ["your-domain", "your-tag"],
    "owner": "product-team"
  },
  "relations": {
    "domain": "growth"
  }
}
```

**Step 3 — Register in root catalog**

Add your feature to `catalog-info.yaml` targets list:
```yaml
- ./features/your-feature-name/catalog-info.yaml
```

**Step 4 — Open a PR**
Fill the PR template checklist. Get it reviewed. Merge. Port syncs automatically within minutes.

---

## Port — Our Product Portal

**Port (getport.io)** is the visual UI layer on top of this repo. Every time you merge to `main`, Port reads the `.port/entities/` folder and updates the catalog automatically. You edit here in GitHub — you view and manage in Port.

### Feature 1 — Software Catalog

A searchable, filterable table of all CashKaro features. Each row shows the feature name, lifecycle stage, owner, domain, and quick links to Figma and Confluence. Stakeholders get a single URL to see everything at once.

### Feature 2 — AI Search

Port has a natural language search layer over the entire catalog. You can ask things like:

- *"Which features are currently in development?"*
- *"Show me all features owned by the product team in the growth domain"*
- *"Which features have no Figma link?"*
- *"What is the status of SevaKaro?"*

No filters, no queries — just ask in plain English.

### Feature 3 — MCP (AI Coding Agent Integration)

Port exposes an MCP (Model Context Protocol) server. This means AI coding tools like Claude Code can connect directly to Port and query the catalog while you're building. An agent can ask Port "what is the spec for SevaKaro?" and get back structured data from the catalog — without you having to paste docs manually.

This is the AI-readable layer working at its best: the repo is the source of truth, Port is the API, and the AI agent uses it in real time.

### Feature 4 — Scorecards (Rules Enforcement)

Scorecards are rules you define that automatically grade every feature. Features progress from Basic → Bronze → Silver → Gold based on how complete they are.

Example scorecard for CashKaro features:

| Level | Rules to pass |
|-------|--------------|
| **Basic** | Has a description, has an owner, lifecycle is set |
| **Bronze** | PRD exists, Figma link is filled, domain is set |
| **Silver** | Success metrics defined, DRD exists, no open questions |
| **Gold** | Test plan exists, lifecycle is `production`, data instrumentation defined |

Any feature that doesn't meet a level shows a red/yellow indicator in the catalog. PMs can see at a glance what's missing before asking engineering to start.

### Feature 5 — Dashboards

Custom dashboards built on top of the catalog. Examples we can build:

- **Feature pipeline** — how many features are in each lifecycle stage right now
- **Domain health** — which domains have the most features in `concept` vs `production`
- **Completeness tracker** — scorecard compliance across all features
- **Ownership map** — which PM owns how many features

### Feature 6 — Self-Service Actions

Buttons in the Port UI that trigger real workflows. Examples:

| Action | What it does |
|--------|-------------|
| "Move to In-Development" | Updates lifecycle in GitHub via PR, notifies engineering on Slack |
| "Create Feature Folder" | Scaffolds the entire feature folder structure in GitHub automatically |
| "Request Design Review" | Creates a Jira ticket and pings the designer |

Actions remove the manual steps between decisions and execution.

### Feature 7 — Automations

Event-driven triggers that run when catalog data changes. Examples:

- Feature lifecycle changes to `in-development` → automatically notify the engineering team
- Feature has no Figma link after 7 days in `concept` → send a reminder to the PM
- New feature entity created → auto-create the folder structure in GitHub

### Feature 8 — Relations Graph

Port visualises the relationships between entities. You can see:
- Which features belong to which domain
- Which domain owns the most in-progress work
- The full product map in a visual graph — useful for stakeholder presentations

---

## Using this repo with AI

Every feature's `docs/` folder is structured to be fed directly to an AI:

```
Give Claude this context before asking it to help you:
→ features/sevakaro/docs/prd.md        (what we're building)
→ features/sevakaro/docs/drd.md        (how it should look)
→ features/sevakaro/docs/decisions.md  (what was already decided)
```

Port's MCP integration takes this further — AI agents can query Port directly without you having to paste anything.
