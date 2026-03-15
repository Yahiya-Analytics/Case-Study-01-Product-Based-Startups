# Case Study 02 — Myntra: The "End of Reason" Return Spike

**Company:** Myntra (E-commerce Fashion)  
**Domain:** Supply Chain Analytics · Reverse Logistics · Consumer Behavior  
**Analyst:** Syed Yahiya Ahmed  
**Difficulty:** Guided  
**Status:** ✅ Complete

> **TL;DR:** Investigated a scenario where Gross Sales hit record highs during a major sale, but Net Profits tanked due to a Return Rate spike from 22% to 35%. Segmented the data to discover that loyal existing users (Myntra Insiders) were exploiting a "Flat 50% off on carts above ₹3,000" promotion by "bracketing" (buying multiple sizes of one item to cross the threshold, then returning the rest). Recommended implementing Pro-Rated Refunds and a targeted Reverse Pickup Fee to eliminate the loophole without hurting genuine conversions.

---

## The Meeting

The VP of Supply Chain & Operations calls you into a meeting. She looks stressed.

> *"During our recent 'End of Reason Sale', Gross Sales (GMV) hit record highs. Marketing is celebrating. But my logistics team is bleeding money, and our Net Profit is down. I looked at the dashboard, and our overall Return Rate has spiked to 35% this quarter, up from our normal baseline of 22%. Figure out what's driving these returns and how we fix it."*

In E-commerce, returns (reverse logistics) are the silent killers of profit margins. The goal isn't just to find out *what* is being returned, but *why* the behavior suddenly changed.

---

## Act 1 — Scoping the Operations

Before blaming the customer, a good analyst checks internal systems.

**Q: Did something break internally? How was inventory and fulfillment managed this quarter vs last?**  
A massive spike in returns could be caused by a broken quality check process, a bad batch of inventory, or a faulty delivery partner.  
→ *Confirmed: Operations, warehousing, and delivery partners were perfectly stable. This was not a system failure. The problem was customer-driven.*

With internal operations ruled out, the strategy shifted to **"Cut the Data"** — segmenting the 35% overall return rate to find the exact anomaly.

---

## Act 2 — Slicing the Data (Who & What)

**Cut 1: By User Cohort (Who is returning?)**
| User Segment | Normal Return Rate | Sale Quarter Return Rate | Status |
|-------------|-------------------|--------------------------|--------|
| New Users | ~20% | 24% | Normal (Expected during sales) |
| **Existing Users (Insiders)** | ~23% | **42%** | **🚨 Massive Anomaly** |

The spike was entirely driven by the most loyal, existing customers. 

**Cut 2: By Product Category (What are they returning?)**
Looking strictly at the Existing Users cohort:
*   Beauty & Personal Care: 8% (Normal)
*   Electronics & Accessories: 12% (Normal)
*   Home Decor: 15% (Normal)
*   **Apparel & Footwear:** **60% (🚨 Spiked from 30%)**

The leak was completely isolated. Existing users were returning 60% of the clothing and shoes they bought. But why?

---

## Act 3 — The Order-Level Deep Dive

To understand the *Why*, we pulled a sample of 1,000 orders placed by Existing Users containing Apparel/Footwear during the sale, comparing them to a normal quarter.

| Metric (Per Order Average) | Normal Quarter | 'End of Reason Sale' |
| :--- | :--- | :--- |
| **Total Items in Cart** | 2.1 items | **4.5 items** |
| **Average Order Value (Gross)** | ₹1,800 | **₹3,600** |
| **Items Returned per Order** | 0.5 items | **2.8 items** |
| **Net Items Kept per Order** | 1.6 items | 1.7 items |

**The SQL Query Revelation:**
In 65% of these high-return orders, the customer bought **the exact same item (same brand, style) in two or three different sizes.** (e.g., Puma Sneaker in Size 8, Size 9, and Size 10). 

Furthermore, pulling the "Return Reason Codes" showed that **80% of these returns were tagged as "Size/Fit Issue".**

Customers were using Myntra's delivery drivers as a free, at-home fitting room—a behavior known in E-commerce as **"Bracketing."** 

---

## Act 4 — Connecting the Loophole

Why did loyal users suddenly start bracketing *now*? The answer was hidden in the Marketing team's promotional rules.

Marketing had sent a push notification to Insiders:  
> **"VIP EARLY ACCESS! Get a FLAT 50% OFF your entire cart—but only if your cart value is above ₹3,000!"**

**The Customer Psychology (Gaming the System):**
1. Customer wants a ₹1,500 jacket (No discount applied).
2. Customer artificially inflates their cart by adding the same jacket in two other sizes (Cart value = ₹4,500).
3. The ₹3,000 threshold is crossed. The 50% discount applies. Customer pays ₹2,250.
4. Customer receives the items, keeps the correct size, and returns the other two jackets.
5. Customer gets a refund for the returned items, ultimately securing their ₹1,500 jacket for just ₹750.

Marketing saw higher Gross Sales (GMV) and higher Average Order Value (AOV). But Supply Chain was left paying the reverse logistics costs for millions of dummy items.

---

## Act 5 — The Recommendation

The problem was not fraud (which requires strict operational fixes like Open-Box Delivery). The problem was **Exploitative Intent** caused by a mathematical loophole in the policy. 

**Recommended Actions:**

**1. Implement "Pro-Rated Refunds" (Discount Reversal)**  
Fix the backend refund logic. If a customer returns items and their *net kept cart value* drops below the ₹3,000 promotional threshold, the system automatically revokes the 50% discount on the kept items. The refund amount is adjusted accordingly. Once the financial incentive to bracket is removed, the behavior stops.

**2. Introduce Targeted Friction (Reverse Pickup Fee)**  
To permanently discourage bracketing, introduce a ₹50–₹100 Reverse Pickup Fee. However, to avoid damaging the user experience for honest buyers, this fee should only trigger dynamically for users who have a historical return rate exceeding 40%. 

---

## What This Case Taught

**1. High GMV can hide bad Unit Economics.**  
A spike in Gross Sales or Average Order Value (AOV) is not always a win. If it is driven by artificial cart inflation that results in high returns, the logistics cost will wipe out the net profit. 

**2. Intent vs. Fraud requires different solutions.**  
Fraud (stealing) requires operational friction like OTPs or Open-Box delivery. Exploitative Intent (gaming policies) requires mathematical friction like adjusting refund logic or adding fees. Applying a fraud solution to an intent problem ruins the customer experience and skyrockets delivery times.

**3. "Bracketing" is the biggest threat to Fashion E-commerce.**  
The Fit-Risk of apparel makes it highly susceptible to bracketing. When analyzing returns, always split standardized items (electronics) from fit-dependent items (clothing) immediately.

**4. Friction is a dial, not a switch.**  
Free returns maximize Conversion but destroy Margins. Paid returns maximize Margins but hurt Conversion. A Data Analyst's job is to find the perfect middle ground—applying targeted friction only to high-risk cohorts.

---

## Framework Reference

```text
E-COMMERCE METRICS BREAKDOWN:

Gross Sales (GMV) = Total Value of all items checked out
Net Sales = Gross Sales - Returns - Cancellations
Unit Economics = (Net Revenue per item) - (COGS + Delivery + Reverse Logistics Cost)
```

```text
THE "CUT THE DATA" FRAMEWORK FOR ANOMALIES:

Spike in Metric (e.g., Return Rate)
    ├── 1. By User Cohort (New vs. Existing / High LTV vs. Low LTV)
    ├── 2. By Product Category (Apparel vs. Electronics)
    └── 3. By Geography/Logistics (Tier 1 vs. Tier 2 / COD vs. Prepaid)
```

---

*Next: [Case Study 03 — Coming Soon]*
