# Case Study 01 — Zomato: The Invisible Revenue Leak

**Company:** Zomato  
**Domain:** Food Delivery · Revenue Analysis · Growth Analytics  
**Analyst:** Syed Yahiya Ahmed  
**Difficulty:** Guided  
**Status:** ✅ Complete

---
**TL;DR** : Investigated a scenario where Q1 order volumes grew 18% but revenue remained flat. Discovered that a "New User" marketing campaign offering flat ₹200 discounts drove a 50% spike in low-value orders, suppressing platform AOV by 20%. Recommended shifting focus from immediate revenue fixes to tracking Q2 Post-coupon Retention Rate and LTV:CAC ratios to evaluate the campaign's true ROI, while implementing a ₹500 minimum order floor for future campaigns.

---
## The Monday Morning Problem

It's the first Monday of Q2. The Head of Growth walks up to the analyst's desk and drops a single sentence:

> *"Our order volumes are up 18% this quarter — but revenue is flat. Figure out what's going on."*

No dashboard. No context. No data pulled yet.

This is the moment that separates a data analyst from a data reporter. A reporter pulls numbers. An analyst asks the right questions before touching a single row.

---

## Act 1 — Before the Data: Asking the Right Questions

The first instinct when hearing "revenue is flat" is to jump to explanations — seasonality, competition, customer behaviour. That instinct is wrong. The first job is to define the problem precisely enough that the data can actually answer it.

**What the analyst established before opening any dashboard:**

**Q: Which revenue stream are we measuring?**  
Zomato runs multiple revenue lines — restaurant advertising, Zomato Gold subscriptions, dining-out, and Core Food Delivery commissions. "Revenue is flat" means nothing until the stream is named.  
→ *Confirmed: Core Food Delivery only. This includes restaurant commissions (% of order value) and customer platform/delivery fees.*

**Q: Is this a national trend or location-specific?**  
A pan-India flat revenue reading could mask a regional collapse or a regional boom cancelling out a regional drop.  
→ *Confirmed: Pan-India. All major metros showing the same pattern.*

**Q: What is the comparison baseline?**  
Q1 vs Q4 (previous quarter) — not year-on-year. This matters because Q1 (Jan–Mar) carries wedding season demand which inflates order volumes seasonally.

With scope locked, the analyst wrote down the only formula that matters:

```
Total Food Delivery Revenue = Total Orders × AOV × Take Rate

Where:
  AOV       = Average Order Value (food cart value in ₹)
  Take Rate = Zomato's commission % charged to restaurants
              + customer platform/delivery fees
```

**The arithmetic already told a story.**

If Total Orders went UP 18% and Total Revenue stayed FLAT (0% growth) — then Average Revenue Per Order must have gone DOWN. There is no other mathematical possibility.

This single insight — derived from the formula before any data was pulled — gave the entire investigation its direction.

---

## Act 2 — Following the Rupee

To understand what drives Revenue Per Order, the analyst mapped a single ₹500 transaction through the Zomato system:

```
Customer pays:  ₹500 (food) + ₹50 (platform + delivery fee)
                = ₹550 total

Zomato earns:   ₹50  (customer fees)
              + ₹100 (20% commission on ₹500 food value)
                = ₹150 Revenue per Order

Restaurant gets: ₹400
Delivery partner gets: ~₹40 (from Zomato's cost base)
```

This means Revenue per Order has exactly three levers:

| Lever | What it is | Direction needed to cause flat revenue |
|-------|-----------|---------------------------------------|
| AOV | Value of food in the cart | Must have gone ↓ |
| Take Rate | Commission % Zomato charges restaurants | Must have gone ↓ |
| Customer Fees | Platform fee + delivery fee per order | Must have gone ↓ |

The analyst checked each one.

**Take Rate:** Pulled commission data for Q1 vs Q4. Restaurant commission held steady at **20%** across both quarters. Not the driver.

**Customer Fees:** Platform fee structure unchanged. Not the driver.

**AOV:** This is where the number moved.

---

## Act 3 — The Data Reveals the Leak

With two levers ruled out, the data team pulled Q1 vs Q4 AOV numbers:

| Metric | Q4 | Q1 | Change |
|--------|----|----|--------|
| Average Order Value (AOV) | ₹400 | ₹320 | **▼ 20%** |
| Zomato Discount Spend | Baseline | +45% vs Q4 | **▲ Significant** |
| New User Order Volume | Baseline | +50% vs Q4 | **▲ Spike** |
| Existing User AOV | ₹400 | ₹400 | **Stable** |
| Existing User Order Volume | Baseline | +5% vs Q4 | Normal growth |

The AOV had dropped 20% quarter-on-quarter. But existing users — people who had ordered before — showed no change in behaviour whatsoever. Their AOV held at ₹400 and their volumes grew a normal 5%.

The entire anomaly came from **new users**.

New user order volumes had spiked **50%** in Q1 — but their Average Order Value was only **₹200**, exactly half the platform average.

The analyst dug one level deeper. Why were new users ordering at half the cart value of existing users?

---

## Act 4 — The Root Cause

The Marketing team had run a **"New Year, New User"** campaign in Q1 — a flat ₹200 discount applied to the first 3 orders for any new sign-up on the platform.

The mechanics of how this destroyed AOV:

```
New user places ₹400 order
Applies ₹200 coupon
Cart value paid by user: ₹200
Zomato's commission (20% of ₹400): ₹80
Minus ₹200 discount funded by Zomato: -₹200
Net Revenue per Order: -₹120
```

Zomato was **losing money on every new user order** during the campaign period. The 50% spike in new user volumes — which inflated the total order count and produced the headline "18% volume growth" — was generating near-zero or negative revenue per order.

The volume growth number was real. The implicit assumption that volume growth = revenue growth was not.

**The core finding in one sentence:**  
*A ₹200 flat-discount new-user acquisition campaign drove a 50% spike in new user orders, suppressed platform AOV by 20% (₹400 → ₹320), and kept total revenue flat despite 18% more orders being placed — because each discounted order contributed near-zero revenue.*

---

## Act 5 — Was This Actually a Problem?

Before recommending the campaign be stopped, the analyst asked the question that separates junior from senior thinking: **is this a bad thing, or is it a planned strategic investment?**

Startups routinely accept short-term revenue suppression to acquire users who will generate long-term value. The question is not whether the campaign cost money. The question is: **will these users stick around after the discounts run out?**

This reframes the entire investigation. The real metric is not Q1 revenue. It is **Q2 Retention Rate of the new user cohort.**

```
If new user places Order #4 at full price in Q2:
  → Campaign was an investment. CAC was justified.

If new user disappears after Order #3:
  → Campaign bought temporary volume, not customers.
     CAC was wasted spend.
```

---

## Act 6 — The Recommendation

**Immediate actions (within current quarter):**

Do not cancel the campaign mid-quarter — cutting it abruptly damages user trust and wastes the acquisition spend already made. Let it complete.

Implement a **minimum order value threshold of ₹500** for coupon eligibility going forward. This protects AOV while still offering an acquisition incentive. A user who builds a ₹300 cart will be motivated to add ₹200 more to unlock the discount — lifting AOV rather than suppressing it.

**Track these metrics in Q2 to evaluate campaign ROI:**

| Metric | Definition | Target threshold |
|--------|-----------|-----------------|
| **Post-coupon Retention Rate** | % of new Q1 users who place Order #4 at full price in Q2 | > 40% = campaign justified |
| **LTV:CAC Ratio** | Projected 12-month revenue from new user ÷ acquisition cost per user | > 3× = healthy unit economics |
| **Cart Abandonment Rate** | % of sessions where user builds cart but does not complete order | Monitor after ₹500 minimum threshold is applied |
| **New User AOV (Month 2)** | AOV of Q1 new users in their first full-price month | Should trend toward platform average of ₹400 |

**Decision rule for Q3 campaign planning:**

```
Retention Rate > 40% AND LTV:CAC > 3×
  → Campaign was profitable. Repeat with ₹500 minimum order floor.

Retention Rate < 20% OR LTV:CAC < 2×
  → Campaign bought volume only. Shift budget to existing 
     user engagement (Zomato Gold upsell, loyalty rewards).
```

---

## What This Case Taught

**1. Volume and Value are independent variables.**  
Orders up 18% is a volume metric. Revenue per order is a value metric. They can — and often do — move in opposite directions. Always decompose: `Revenue = Orders × AOV × Take Rate` before forming any hypothesis.

**2. Scope questions come before hypotheses.**  
The first question asked — *which revenue stream?* — prevented 30 minutes of analysis on the wrong dataset. One scoping question saved an entire investigation thread.

**3. Segment new users vs existing users immediately.**  
Whenever marketing spend or discount usage spikes, the first cut is always New vs Existing. Their behaviour is structurally different. Mixing them in aggregate metrics hides the truth.

**4. CAC goes up when discounts go up, not down.**  
Giving a user ₹200 in coupons means the cost to acquire that user is at minimum ₹200 — plus ad spend. Higher discounts = higher CAC. Always.

**5. Diagnose before prescribing.**  
The instinct to immediately recommend "reduce discounts" was premature. The campaign may have been a deliberate strategic investment. Checking whether it was planned — and building a retention-based ROI framework to evaluate it — is the difference between an analyst and an advisor.

---

## Framework Reference

```
TOTAL REVENUE DECOMPOSITION — FOOD DELIVERY

Total Revenue
    └── Orders × Revenue per Order
              └── (AOV × Take Rate) + Customer Fees
                        └── New Users vs Existing Users
                                  └── Discounted vs Full Price Orders
```

```
CAC vs LTV DECISION RULE

CAC  = Total discount + ad spend per acquired user
LTV  = Avg monthly revenue per user × avg retention months
Ratio = LTV ÷ CAC

Healthy: LTV ≥ 3× CAC
Warning: LTV between 1.5–3× CAC  
Unsustainable: LTV < 1.5× CAC
```

---

*Next: [Case Study 02 — Myntra Return Rate Analysis](../case-study-02-myntra-returns/README.md)*
