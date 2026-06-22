# Test Plan — SevaKaro

**Version:** 0.1  
**Last Updated:** 2026-06-22  
**Status:** Draft

---

## 1. Scope

What is being tested in this round:
- Charity discovery and browsing
- Donation flow end-to-end
- Wallet deduction accuracy
- Error handling
- Analytics event firing

---

## 2. Test Cases

### Functional Tests

| ID | Scenario | Steps | Expected Result |
|----|---------|-------|----------------|
| TC-01 | Happy path donation | Open SevaKaro → pick charity → enter ₹50 → confirm | Wallet debited ₹50, success screen shown, donation in history |
| TC-02 | Donate full balance | Enter amount = full wallet balance | Wallet shows ₹0, success screen shown |
| TC-03 | Amount below minimum | Enter ₹5 | CTA disabled, "Minimum donation is ₹10" shown |
| TC-04 | Amount above wallet balance | Enter amount > balance | CTA disabled, "Insufficient balance" shown |
| TC-05 | API failure mid-flow | Simulate network error on confirm | Wallet NOT debited, error message shown, retry available |
| TC-06 | Empty wallet state | Open SevaKaro with ₹0 balance | "Earn more cashback first" message, CTA disabled |
| TC-07 | Charity list loads | Open SevaKaro landing | All charities load within 2 seconds |
| TC-08 | Donation history | Complete donation → open history | Donation appears with correct amount, charity, and timestamp |

### Analytics Tests

| ID | Event | Trigger | Verify |
|----|-------|---------|--------|
| AT-01 | `sevakaro_page_viewed` | Open landing page | Fires once with `source` property |
| AT-02 | `donation_completed` | Successful donation | Fires with correct `amount` and `charity_id` |
| AT-03 | `donation_failed` | API error | Fires with `error_code` |

---

## 3. Device Matrix

| Device | OS | Browser/App |
|--------|-----|------------|
| Android (mid-range) | Android 11 | CashKaro app |
| Android (flagship) | Android 14 | CashKaro app |
| iPhone | iOS 16 | CashKaro app |
| Desktop | Chrome | Web (if applicable) |

---

## 4. Acceptance Criteria

Feature is ready to ship when:
- [ ] All P0 test cases pass
- [ ] All analytics events fire correctly
- [ ] Wallet deduction is accurate to the paisa
- [ ] No crash on any device in matrix
- [ ] Load time < 2 seconds on 4G
