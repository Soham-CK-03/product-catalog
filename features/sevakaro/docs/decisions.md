# Decisions — SevaKaro

Architecture Decision Records (ADRs). Each decision is permanent — if reversed, add a new ADR that supersedes it. Never edit a past ADR.

---

## ADR-001: Wallet-only donations in v1 (no external payments)

**Date:** 2026-06-22  
**Status:** Accepted

### Context
Users could donate either from their CashKaro wallet balance or via fresh UPI/card payment.

### Decision
v1 supports wallet balance only.

### Reasoning
- Simplest to implement — no payment gateway integration needed
- Aligns with the positioning ("turn your cashback into good")
- Reduces fraud risk
- If traction is proven, UPI can be added in v2

### Consequences
- Users with wallet balance < ₹10 cannot donate
- UPI payment path deferred to v2

---

## ADR-002: Minimum donation set to ₹10

**Date:** 2026-06-22  
**Status:** Draft — pending data analysis

### Context
We need a minimum donation amount. Options: ₹1, ₹5, ₹10, ₹50.

### Decision
₹10 (pending validation — see open question in PRD)

### Reasoning
- Below ₹10, transaction overhead approaches the donation value
- ₹10 feels like a real contribution to users
- Most Indian donation platforms use ₹10 as floor

### Consequences
- Users with < ₹10 balance cannot donate — we show an empty state with "Earn more cashback first"

---

_Add new ADRs as decisions are made._
