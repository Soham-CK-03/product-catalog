# Data Analysis — Store Page

**Last Updated:** 2026-06-22

---

## 1. Current Funnel

```
Store page views (monthly)        ~2.4M
  |  22% Shop Now CTR
Shop Now clicks                   ~528K
  |  ~18% transaction rate
Cashback transactions             ~95K
  |  avg Rs.85 cashback
Total cashback paid out           ~Rs.80L/month
```

**Opportunity:** If CTR improves from 22% to 28% (our target), that's ~144K additional Shop Now clicks/month, potentially ~26K additional transactions.

---

## 2. Instrumentation Plan

Every interaction must fire an analytics event. Defined before engineering starts.

| Event | Trigger | Properties |
|-------|---------|-----------|
| `store_page_viewed` | Page load complete | `store_id`, `store_name`, `source` |
| `cashback_rate_seen` | Rate hero scrolled into view | `store_id`, `rate` |
| `shop_now_clicked` | Shop Now CTA tapped | `store_id`, `cashback_rate` |
| `coupon_viewed` | Coupon card visible | `store_id`, `coupon_id`, `position` |
| `coupon_copied` | Copy button tapped | `store_id`, `coupon_id`, `coupon_code` |
| `coupon_expanded` | User opens full coupon list | `store_id`, `visible_count` |
| `store_page_bounced` | User leaves with no interaction | `store_id`, `time_on_page` |

---

## 3. A/B Tests Planned

| Test | Variant A (control) | Variant B (test) | Primary metric |
|------|---------------------|------------------|----------------|
| Cashback rate size | Current (small) | Hero (32px, green bg) | Shop Now CTR |
| Coupon count above fold | 5 coupons | 3 coupons | Coupon copy rate |
| CTA copy | "Shop Now" | "Shop Now & Earn Cashback" | CTR |

---

## 4. Post-Launch Tracking

| Metric | Week 1 | Week 2 | Week 4 |
|--------|--------|--------|--------|
| Shop Now CTR | — | — | — |
| Bounce rate | — | — | — |
| Page load time | — | — | — |
| Coupon copy rate | — | — | — |
| Cashback transactions | — | — | — |
