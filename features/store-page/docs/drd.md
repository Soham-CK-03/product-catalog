# DRD — Store Page

**Version:** 0.1
**Designer:** [Add designer name]
**Last Updated:** 2026-06-22
**Figma:** [Replace with actual Figma link](#)

---

## 1. Design Principles

- **Cashback first** — the rate must be the largest, most prominent element on the page
- **3-second rule** — a user must understand the page value in 3 seconds or less
- **Zero clutter above the fold** — only logo, cashback rate, and Shop Now CTA

---

## 2. Screens Required

| Screen | Priority |
|--------|----------|
| Store page — default state | P0 |
| Store page — no coupons state | P0 |
| Store page — 0% cashback state | P0 |
| Store page — suspended state | P0 |
| Coupon copied — toast confirmation | P0 |
| Not logged in — blurred CTA state | P1 |

---

## 3. Layout — Above the Fold

```
+------------------------------------------+
|  [Store Logo 80x80]                       |
|  Amazon                                   |
|  ★★★★☆  4.2 · Electronics & More          |
|                                           |
|  ┌──────────────────────────────────┐    |
|  │   Up to 8% Cashback              │    |
|  │   on all purchases               │    |
|  └──────────────────────────────────┘    |
|                                           |
|  [  Shop Now & Earn Cashback  ] ←CTA     |
|                                           |
|  TOP COUPONS                              |
|  +----------+ +----------+ +----------+  |
|  | SAVE200  | | FLAT10   | | NEW500   |  |
|  | Rs.200 off| |10% off  | |Rs.500 off|  |
|  | [Copy]   | | [Copy]  | | [Copy]   |  |
|  +----------+ +----------+ +----------+  |
+------------------------------------------+
```

---

## 4. Component Specifications

### Cashback Rate Hero
- Font size: 32px bold
- Color: CashKaro green `#2ECC71`
- Sub-label: 14px grey — "on all purchases via CashKaro"
- Background: light green tint `#F0FFF4`
- Border radius: 12px

### Shop Now CTA Button
- Full width
- Height: 52px
- Background: `#2ECC71`
- Text: "Shop Now & Earn Cashback" — 16px bold white
- Icon: external link icon on right

### Coupon Card
- Width: 1/3 of screen (3 per row)
- Code in monospace bold
- Discount label below
- Verified badge (blue tick) if verified
- Copy button — triggers clipboard + toast

### Coupon Copy Toast
- "Code copied!" — appears for 2 seconds
- Bottom of screen
- Green background

---

## 5. Figma Links

| Asset | Link |
|-------|------|
| Full page design | [Replace with Figma link](#) |
| Component specs | [Replace with Figma link](#) |
| Prototype | [Replace with Figma link](#) |

---

## 6. Open Design Questions

- [ ] Should the cashback rate hero use an animation to draw attention?
- [ ] Mobile vs desktop — same layout or different?
- [ ] How do we visually differentiate app-exclusive cashback from standard?
