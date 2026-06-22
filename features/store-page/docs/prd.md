# Store Page — PRD

**Version:** 0.2 (In Review)
**Author:** Product Team
**Last Updated:** 2026-06-22
**Status:** In Development

---

## 1. Problem Statement

The current CashKaro store page has three critical problems:

1. **Cashback rate is not prominent** — users scroll past it or miss it entirely. The cashback rate is the #1 reason users come to CashKaro, yet it is displayed in small text below the fold.
2. **Coupon section is overwhelming** — 20+ coupons shown in a flat list with no ranking, expired coupons mixed with active ones, and no indication of which ones are most used.
3. **Page load time is 4-6 seconds on 4G** — users drop off before the page finishes loading. Direct affiliate links get more clicks than CashKaro because of this.

---

## 2. Goals

- Make the cashback rate the first thing users see and understand
- Surface the 3 best coupons above the fold, ranked by usage
- Reduce page load time to under 2 seconds on 4G
- Increase "Shop Now" CTA click-through rate by 20%

---

## 3. Non-Goals (v1)

- Personalised coupon ranking per user (v2)
- Store comparison feature (v2)
- Price tracking / price history (separate feature)
- Brand advertising / sponsored placement

---

## 4. User Stories

| # | As a... | I want to... | So that... |
|---|---------|-------------|-----------|
| US-01 | CashKaro user | See the cashback rate immediately on landing | I know what I will earn before clicking through |
| US-02 | CashKaro user | See the top 3 coupons without scrolling | I can quickly decide which coupon to use |
| US-03 | CashKaro user | Know which coupons are verified and active | I don't waste time on expired codes |
| US-04 | CashKaro user | Click Shop Now and land on the right store page | I can start shopping in one tap |
| US-05 | Returning user | See if the cashback rate has changed since my last visit | I know if now is a good time to buy |

---

## 5. Success Metrics

| Metric | Baseline | Target | How to measure |
|--------|----------|--------|----------------|
| Shop Now CTR | 22% | 28% | `shop_now_clicked` / `store_page_viewed` |
| Bounce rate | 58% | 45% | Users who leave without any interaction |
| Page load time (4G) | 4.8s | < 2.0s | Lighthouse / field data |
| Coupon copy rate | 12% | 18% | `coupon_copied` / `store_page_viewed` |
| Cashback transaction volume | baseline | +15% | Weekly cashback transactions from store |

---

## 6. Scope

### In Scope
- Hero section: store logo, cashback rate (large), Shop Now CTA
- Top 3 coupons ranked by redemption count, verified badge, copy button
- All coupons section (below fold) — active only, sorted by newest
- Store info section: category, avg cashback, last updated timestamp
- Similar stores section (bottom)

### Out of Scope
- User reviews of the store
- Price comparison
- Personalised recommendations
- App-exclusive cashback badge (already exists, keep as-is)

---

## 7. User Flow

```
Search / Home / Category page
    |
Store Page
    |
[Hero] Store logo + Cashback Rate (e.g. "Up to 8% Cashback") + Shop Now CTA
    |
[Top Coupons] 3 cards — code, discount, verified badge, copy button
    |
[All Coupons] Flat list, active only, newest first
    |
[Store Info] About, category, last updated
    |
[Similar Stores] Horizontal scroll
```

---

## 8. Edge Cases

| Case | Handling |
|------|---------|
| Store has no active coupons | Hide coupon section, show "No coupons right now — just use the cashback link" |
| Cashback rate is 0% | Show "Currently no cashback" in red |
| Store is temporarily suspended | Show banner: "Cashback tracking paused for this store" |
| User not logged in | Show cashback rate but blur Shop Now CTA with "Login to earn cashback" |

---

## 9. Open Questions

- [ ] Should we show cashback rate as a range (2%-8%) or a flat rate?
- [ ] Do we rank coupons by redemption count or by discount value?
- [ ] Should expired coupons be hidden completely or shown greyed out?

---

## 10. Dependencies

| Dependency | Team | Status |
|-----------|------|--------|
| Coupon ranking API (sort by redemption) | Engineering | To be built |
| Page speed optimisation (image lazy load) | Engineering | In progress |
| Store suspension flag in CMS | Ops | Exists |
