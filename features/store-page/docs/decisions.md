# Store Page — Decisions

---

## ADR-001: Show cashback rate as a range, not a flat number

**Date:** 2026-06-22
**Status:** Accepted

### Context
Some stores have tiered cashback (e.g. 2% on electronics, 8% on fashion). We can show a flat average or a range.

### Decision
Show as "Up to X% Cashback" where X is the highest available rate.

### Reasoning
- "Up to 8%" is more compelling than "avg 4%"
- Users who click through will see the breakdown on the store
- All major competitors use "up to" framing

### Consequences
- Must show a breakdown tooltip so users understand it is a range
- Needs a new API field: `max_cashback_rate`

---

## ADR-002: Rank coupons by redemption count, not discount value

**Date:** 2026-06-22
**Status:** Accepted

### Context
Two ranking options: sort by discount value (highest first) or by how many users have successfully used it (redemption count).

### Decision
Rank by redemption count (last 30 days).

### Reasoning
- A high-value coupon that never works is worse than a lower-value coupon that always works
- Redemption count is a proxy for trust and success rate
- Aligns with user research finding that coupon trust is the #1 issue

### Consequences
- Need to track redemption count per coupon in the backend
- Ranking updates daily, not real-time
