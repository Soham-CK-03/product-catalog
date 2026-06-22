# SevaKaro — Data Analysis

**Last Updated:** 2026-06-22

---

## 1. Opportunity Sizing

_Pull from internal analytics. Questions to answer:_

| Question | Data Needed | Owner |
|----------|-------------|-------|
| How many users have wallet balance > ₹10? | Wallet balance distribution | Analytics |
| What % of wallet balance is idle > 60 days? | Transaction timestamps | Analytics |
| What is total idle balance in the system? | Wallet table aggregate | Analytics |
| What is our DAU/MAU ratio? | Sessions data | Analytics |

---

## 2. Funnel Model (Pre-launch estimate)

```
MAU                          [X users]
  ↓ 5% discover SevaKaro
SevaKaro page visits         [X * 0.05]
  ↓ 20% convert
Donations completed          [X * 0.05 * 0.20]
  ↓ avg ₹50 per donation
Total donation GMV           [X * 0.05 * 0.20 * 50]
```

_Fill in X from internal MAU data._

---

## 3. Instrumentation Plan

Every user action must fire an analytics event. These must be defined before engineering starts.

| Event Name | Trigger | Properties |
|-----------|---------|-----------|
| `sevakaro_page_viewed` | User opens SevaKaro landing | `source` (wallet/home/nav) |
| `charity_viewed` | User opens a charity profile | `charity_id`, `charity_name` |
| `donate_cta_clicked` | User taps "Donate Now" | `charity_id` |
| `donation_amount_entered` | User enters amount | `amount`, `wallet_balance` |
| `donation_confirmed` | User taps final confirm | `charity_id`, `amount` |
| `donation_completed` | Server confirms success | `charity_id`, `amount`, `transaction_id` |
| `donation_failed` | Server returns error | `charity_id`, `amount`, `error_code` |
| `donation_history_viewed` | User opens history tab | — |

---

## 4. Post-launch Tracking

### Weekly Dashboard Metrics

| Metric | Formula |
|--------|---------|
| Activation rate | `sevakaro_page_viewed` unique users / MAU |
| Donation CVR | `donation_completed` / `sevakaro_page_viewed` |
| Avg donation | SUM(`donation_completed.amount`) / COUNT(`donation_completed`) |
| Total GMV | SUM(`donation_completed.amount`) |
| Repeat donor rate | Users with ≥2 `donation_completed` in 30 days / all donors |

---

## 5. A/B Tests Planned

| Test | Hypothesis | Metric |
|------|-----------|--------|
| Entry point: wallet banner vs. home card | Wallet banner will drive higher CTR as user already has balance in mind | CTR on SevaKaro entry point |
| Minimum donation: ₹10 vs. ₹1 | Lower minimum increases conversion | Donation CVR |

---

## 6. Analysis Results

_To be filled post-launch._

| Period | Activation Rate | Donation CVR | GMV |
|--------|----------------|-------------|-----|
| Week 1 | — | — | — |
| Week 2 | — | — | — |
| Month 1 | — | — | — |
