# Test Plan — Store Page

**Last Updated:** 2026-06-22

---

## Test Cases

| ID | Scenario | Expected Result |
|----|---------|----------------|
| TC-01 | Store with cashback > 0% | Rate shown in hero, green background |
| TC-02 | Store with 0% cashback | "Currently no cashback" shown in red |
| TC-03 | Store with no coupons | Coupon section hidden, message shown |
| TC-04 | Store suspended | Banner shown, Shop Now disabled |
| TC-05 | Copy coupon code | Toast confirms, clipboard has code |
| TC-06 | Shop Now click (logged in) | Redirects via tracking link |
| TC-07 | Shop Now click (logged out) | Login prompt shown |
| TC-08 | Page load time on 4G throttle | Loads in < 2 seconds |
| TC-09 | 20+ coupons available | Top 3 shown above fold, rest collapsed |
| TC-10 | Analytics events fire | All events in instrumentation plan fire correctly |

## Acceptance Criteria

- [ ] All P0 test cases pass
- [ ] Page load < 2s on Chrome 4G throttle
- [ ] All analytics events verified in dashboard
- [ ] No layout breaks on Android mid-range device
