# SevaKaro — PRD

**Version:** 0.1 (Draft)  
**Author:** Soham  
**Last Updated:** 2026-06-22  
**Status:** Draft

---

## 1. Problem Statement

CashKaro users accumulate cashback in their wallets. A significant portion of this balance stays idle — users either forget about it or the amounts feel too small to redeem. There is currently no mechanism for users to direct this balance toward a cause they care about.

At the same time, CashKaro has no social impact story. SevaKaro fills both gaps.

---

## 2. Goals

- Allow users to donate wallet balance to verified NGOs directly from the CashKaro app
- Build a social impact narrative for CashKaro
- Increase wallet balance engagement (reduce idle balance)
- Create a path for CSR partnerships with brands

---

## 3. Non-Goals (v1)

- Tax exemption certificates (80G) — v2
- Brand-sponsored charity campaigns — v2
- Social sharing of donations — v2
- Recurring / scheduled donations — v2
- UPI / external payment for donation (only wallet balance in v1)

---

## 4. User Stories

| # | As a... | I want to... | So that... |
|---|---------|-------------|-----------|
| US-01 | CashKaro user | Browse verified charities | I can find a cause I care about |
| US-02 | CashKaro user | See a charity's profile and impact | I trust where my money is going |
| US-03 | CashKaro user | Donate any amount ≥ ₹10 from my wallet | I can contribute even small amounts |
| US-04 | CashKaro user | Receive a donation confirmation | I have proof of my contribution |
| US-05 | CashKaro user | See my donation history | I can track my total giving |
| US-06 | New user | Discover SevaKaro from the homepage | I know this feature exists |

---

## 5. Success Metrics

| Metric | Target (90 days post-launch) | How to measure |
|--------|------------------------------|----------------|
| Activation rate | ≥ 5% of MAU visit SevaKaro | Analytics event: `sevakaro_page_viewed` |
| Donation conversion | ≥ 20% of visitors complete a donation | `donation_completed` / `sevakaro_page_viewed` |
| Repeat donation rate | ≥ 30% of donors donate again within 30 days | User-level cohort |
| Avg donation amount | ≥ ₹50 | `donation_completed.amount` |
| Total donations (GMV) | ₹5L in first 90 days | Sum of `donation_completed.amount` |

---

## 6. Scope

### In Scope
- Charity discovery page (list + search)
- Charity profile page (name, mission, impact stats, logo)
- Donation flow (amount entry → confirm → success)
- Wallet deduction on successful donation
- Donation confirmation screen
- Donation history in user profile
- Entry point from wallet section

### Out of Scope (v1)
- 80G tax certificate generation
- External payment methods (only wallet)
- Brand-sponsored drives
- Social sharing
- Admin dashboard for charity management (internal tool, separate scope)

---

## 7. User Flow

```
Home / Wallet
    ↓
SevaKaro landing page
    ↓
Browse charities (categories: Education, Health, Environment, Animals, Women)
    ↓
Charity profile page
    ↓
"Donate" CTA
    ↓
Amount entry screen (min ₹10, max = wallet balance)
    ↓
Confirm donation screen (charity name, amount, wallet balance after)
    ↓
[API: deduct wallet, record donation]
    ↓
Success screen (impact message, "Share" CTA for v2)
    ↓
Donation appears in history
```

---

## 8. Entry Points

| Entry point | Priority |
|-------------|----------|
| Wallet screen — "Donate to a cause" banner | P0 |
| Home screen — SevaKaro card | P1 |
| Bottom navigation tab | P2 |

---

## 9. Edge Cases

| Case | Handling |
|------|---------|
| Wallet balance < ₹10 | Disable donation CTA, show "Earn more cashback first" |
| Payment fails mid-flow | No deduction, show error, allow retry |
| Charity becomes inactive | Hide from discovery, existing donations unaffected |
| User donates full balance | Wallet shows ₹0, confirmation still sent |

---

## 10. Open Questions

- [ ] Do we need legal sign-off on charity verification process before launch?
- [ ] Who manages the charity onboarding (internal ops or external agency)?
- [ ] Should minimum donation be ₹10 or ₹1?
- [ ] Do we show donation amounts publicly (leaderboard) or keep private?

---

## 11. Dependencies

| Dependency | Team | Status |
|-----------|------|--------|
| Wallet deduction API | Engineering | Exists — needs new endpoint for donation type |
| Charity data ingestion | Ops | To be scoped |
| Email confirmation | Notifications team | Exists — needs new template |
