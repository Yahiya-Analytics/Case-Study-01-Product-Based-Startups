# 📊 Product Analytics Case Studies

**Author:** Syed Yahiya Ahmed  
**Focus:** Indian Product Startups — Food Delivery · E-commerce · Fashion · Ride-hailing · Logistics  
**Portfolio:** [yahiya-711.github.io](https://yahiya-711.github.io) · [LinkedIn](https://www.linkedin.com/in/syed-yahiya-ahmed-515920299)

---

## What this repo is

Every case study in this repo is structured exactly the way analytics interviews run at companies like Zomato, Meesho, Fractal Analytics, Tredence, and Deloitte USI — starting from a one-line business problem, working through structured questioning, mathematical decomposition, root cause identification, and ending with a measurable business recommendation.

The framework used in every case:

```
Problem Statement
      ↓
Clarifying Questions  (scope before segment before hypothesis)
      ↓
Mathematical Decomposition  (break the metric into its formula)
      ↓
Root Cause Identification  (data-driven, not assumption-driven)
      ↓
Business Recommendation  (with trackable success metrics)
```

---

## Case Study Index

| # | Company | Domain | Problem Statement | Business Impact | Status |
|---|---------|--------|-------------------|-----------------|--------|
| 01 | **Zomato** | Food Delivery | Order volume ↑18% but revenue flat — diagnose the leak | AOV suppressed 20% by discount campaign · ₹200 CAC per new user · Retention risk in Q2 | ✅ Complete |
| 02 | **Myntra** | Fashion / Retail | Return rate has crossed 35% this quarter — margin is under pressure | High return rate eroding net revenue · fulfilment cost per returned unit directly impacts EBITDA | 🔜 Next |
| 03 | **Flipkart** | E-commerce | GMV is up during Big Billion Days but net revenue margin is shrinking | Discount depth vs incremental revenue trade-off · seller commission compression risk | 🔜 Planned |
| 04 | **Uber** | Ride-hailing | Driver supply is down 22% in Tier-2 cities — surge pricing is hurting retention | Take rate vs driver earnings balance · rider churn from repeated surge pricing events | 🔜 Planned |
| 05 | **Meesho** | Social Commerce | Monthly Active Resellers dropped 18% despite total GMV holding steady | Reseller LTV compression · top-heavy GMV concentration risk in supplier base | 🔜 Planned |

---

## Case Study 02 — Myntra (Preview)

> **You are a Data Analyst at Myntra. The Head of Category walks into your weekly sync and says:**
>
> *"Our return rate has crossed 35% this quarter. That's up from 22% last quarter. Gross margins are under pressure and the logistics team is flagging fulfilment costs. Figure out what's driving returns and what we should do about it."*

**Key metrics in scope:**
- Return Rate by Category (Topwear, Footwear, Ethnic, Western)
- Return Rate by Size vs Availability of Size Chart
- Net Revenue = Gross Revenue − (Returns × Refund Value) − Fulfilment Cost per Return
- Repeat Purchase Rate of high-return customers vs low-return customers
- Return Reason Codes (size issue / quality issue / wrong item / changed mind)

**Business impact to quantify:**
A 1% reduction in return rate on ₹500 Cr quarterly GMV = ~₹5 Cr saved in reverse logistics + margin recovery. The goal of this case is to identify which category and which return reason drives the highest recoverable margin.

---

## Case Study 03 — Flipkart (Preview)

> **You are a Data Analyst at Flipkart. Post Big Billion Days, the CFO flags:**
>
> *"Our GMV hit a record ₹32,000 Cr during the sale — but our net revenue margin came in at 1.2%, down from 3.1% in the previous non-sale quarter. The board wants to understand if Big Billion Days is actually profitable."*

**Key metrics in scope:**
- GMV vs Net Revenue vs Gross Margin decomposition
- Discount Depth per Category (Electronics, Fashion, Appliances)
- Incremental Orders (new buyers) vs Cannibalized Orders (existing buyers pulling forward)
- Customer Acquisition Cost during sale vs organic quarter
- Post-sale Retention Rate (did sale buyers return in 60 days?)

**Business impact to quantify:**
If 60% of Big Billion Days orders are from existing customers pulling forward purchases — the sale generated no incremental revenue, only margin compression. This case tests whether sale events create real business growth or just move revenue across quarters.

---

## Case Study 04 — Uber (Preview)

> **You are a Data Analyst at Uber India. The Head of Supply flags:**
>
> *"Driver online hours in Tier-2 cities (Lucknow, Coimbatore, Indore) dropped 22% in the last 6 weeks. Surge multipliers are hitting 3× during peak hours. Rider complaints are up. Figure out what's happening on the supply side."*

**Key metrics in scope:**
- Driver Online Hours by City Tier and Time Slot
- Driver Earnings per Hour (with vs without incentives)
- Surge Frequency and Surge Multiplier distribution
- Rider Cancellation Rate during surge events
- Driver Churn Rate (went offline permanently vs temporarily)
- Incentive Spend per Active Driver Hour

**Business impact to quantify:**
A 22% drop in driver supply in a city of 50K weekly rides = approximately 11K unfulfilled ride requests per week. At ₹180 average fare and 20% take rate, that's ₹3.96 Cr in weekly gross revenue loss. The case tests supply-demand balancing and incentive ROI analysis.

---

## Case Study 05 — Meesho (Preview)

> **You are a Data Analyst at Meesho. The Growth team shares the monthly dashboard:**
>
> *"Monthly Active Resellers dropped from 1.2M to 980K — an 18% fall. But our total GMV held at ₹4,800 Cr. The team thinks it's fine since GMV is stable. You disagree. Make your case."*

**Key metrics in scope:**
- GMV Concentration (what % of GMV comes from top 10% of resellers?)
- Reseller LTV by cohort (Month 1 vs Month 6 vs Month 12)
- Reseller Churn Rate and reason classification
- Average Orders per Active Reseller (trending up or down?)
- Supplier Diversity — are fewer suppliers getting more share?

**Business impact to quantify:**
If GMV is stable but active resellers dropped 18%, the top resellers are doing more volume — a concentration risk. If the top 10% of resellers generate 70%+ of GMV, losing even 5% of them would cause a GMV cliff. This case tests risk identification and early warning metric design.

---

## Concepts covered across all 5 cases

| Concept | Case where it appears |
|---------|----------------------|
| AOV decomposition | Zomato, Flipkart |
| CAC vs LTV framework | Zomato, Flipkart, Meesho |
| Volume vs Value distinction | Zomato, Meesho |
| Return Rate analysis | Myntra |
| Retention cohort tracking | Zomato, Flipkart, Meesho |
| Supply-demand balancing | Uber |
| GMV concentration risk | Meesho, Flipkart |
| Discount depth vs margin trade-off | Zomato, Flipkart, Myntra |
| Segmentation (new vs existing users) | Zomato, Flipkart |
| Incentive ROI analysis | Uber |

---

## How to read each case study

Each case folder contains a single `README.md` written in a **data storytelling format** — what the analyst observed (X), what investigation revealed (Y), and what business decision it enabled (Z). Numbers are real (simulated from realistic Indian market benchmarks). Recommendations are actionable and tied to trackable metrics.

---

*These case studies are part of a broader Data Analyst portfolio. See [projects repo](https://github.com/Yahiya-711) for end-to-end pipeline, statistical audit, and GenAI analytics work.*
