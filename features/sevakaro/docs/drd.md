# SevaKaro — DRD

**Version:** 0.1 (Draft)  
**Designer:** [Add designer name]  
**Last Updated:** 2026-06-22  
**Figma:** [Replace with actual Figma link](#)

---

## 1. Design Principles for This Feature

- **Trust first** — users are donating real money. UI must convey credibility (verified badges, impact numbers, clear confirmation)
- **Low friction** — fewer taps = more donations. No unnecessary screens
- **Emotionally resonant** — this is a giving experience, not a transaction. Language and visuals should feel warm

---

## 2. Screens Required

| Screen | Description | Priority |
|--------|-------------|----------|
| SevaKaro landing | List of charities with categories filter | P0 |
| Charity profile | Mission, impact stats, logo, donate CTA | P0 |
| Donation amount | Amount input, wallet balance shown, min/max | P0 |
| Confirm donation | Summary before final confirm | P0 |
| Donation success | Confirmation with impact message | P0 |
| Donation history | List of past donations in user profile | P1 |
| Empty state — no balance | Message when wallet < ₹10 | P0 |
| Error state | When donation API fails | P0 |

---

## 3. Component Specifications

### Charity Card (on landing page)
- Logo (80x80px, rounded corners)
- Charity name (16px bold)
- One-line mission statement (14px, max 2 lines, truncate)
- Category tag (e.g. "Education")
- Total donations received (social proof)

### Charity Profile Page
- Hero image (full width, 200px height)
- Verified badge (shows NGO is verified)
- Mission statement (full, no truncation)
- Impact stats row: e.g. "1,240 children educated", "₹45L raised"
- Sticky "Donate Now" CTA button at bottom

### Amount Input Screen
- Current wallet balance shown prominently
- Number pad (not keyboard) for amount entry
- Real-time validation: min ₹10, max wallet balance
- "Donate full balance" quick action
- Disabled state if balance < ₹10

### Confirm Screen
- Charity name + logo
- "You're donating ₹[amount] to [charity]"
- Wallet balance after donation
- Two buttons: "Confirm" (primary) and "Go back" (ghost)

### Success Screen
- Celebration animation (Lottie)
- "Thank you, [first name]!"
- Impact message from the charity (e.g. "Your ₹100 will buy 5 meals")
- "View history" and "Donate again" CTAs

---

## 4. Design Tokens to Use

Use existing CashKaro design system. Specific overrides for SevaKaro:

| Token | Value | Reason |
|-------|-------|--------|
| Primary CTA color | `#4CAF50` (green) | Signals positive/giving action |
| Success screen bg | `#F1F8E9` | Warm green tint |
| Verified badge color | `#1976D2` (blue) | Trust signal |

---

## 5. Copy Guidelines

| Element | Guideline | Example |
|---------|-----------|---------|
| CTA button | Active verb, benefit-led | "Donate Now", not "Submit" |
| Success headline | Personal, warm | "You just made a difference, Soham!" |
| Impact message | Specific and tangible | "₹50 buys 2 school books" not "helps education" |
| Error message | Clear and actionable | "Donation failed. Your wallet was not charged. Try again." |

---

## 6. Figma Links

| Asset | Link |
|-------|------|
| Full flow (all screens) | [Replace with Figma link](#) |
| Component library additions | [Replace with Figma link](#) |
| Prototype (clickable) | [Replace with Figma link](#) |

---

## 7. Open Design Questions

- [ ] Do we need a separate SevaKaro logo/branding or use CashKaro's palette?
- [ ] What Lottie animation for success screen?
- [ ] Should category filters be chips or a dropdown?
