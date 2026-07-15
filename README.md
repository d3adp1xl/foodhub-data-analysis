# FoodHub — Food Delivery Data Analysis

Exploratory data analysis of **1,898 food-delivery orders** for a NYC food-aggregator platform, turning raw order data into concrete business decisions: which restaurants qualify for promotions, where delivery times lag, how much revenue the platform nets, and how to fix a large gap in customer feedback.

> **TL;DR:** An end-to-end EDA that answers real operational questions with data. Not just charts — each finding maps to a recommendation the business can act on (target promo restaurants, chase missing ratings, investigate slow weekday deliveries).

**Stack:** Python · pandas · NumPy · Matplotlib · Seaborn

---

## The Business Context

A food aggregator connects customers with many restaurants through one app. To grow, the company needs to understand its own order data: which restaurants and cuisines drive volume, whether delivery times are acceptable, how ratings behave, and where the money comes from. This analysis works through those questions to support smarter decisions on promotions, operations, and customer experience.

## The Data

1,898 orders across 9 fields (order ID, customer ID, restaurant, cuisine, order cost, day of week, rating, food-prep time, delivery time).

| Property | Value |
|---|---|
| Orders | 1,898 |
| Unique restaurants | 178 |
| Missing values | None |
| Most frequent restaurant | Shake Shack (~11.5% of orders) |

## What I Analyzed

- **Univariate:** distributions of order cost, prep time, delivery time, ratings, cuisine, and day of week (histograms, boxplots, countplots).
- **Multivariate:** relationships between cost, prep time, delivery time, cuisine, and rating — correlation checks and grouped comparisons.
- **Business questions:** promo eligibility, net revenue, delivery-time SLAs, top customers, weekend vs. weekday patterns.

## Key Findings

**Demand is concentrated.** The top 5 restaurants (Shake Shack, The Meatball Shop, Blue Ribbon Sushi, Blue Ribbon Fried Chicken, Parm) pull a large share of orders, and **American and Japanese** are the dominant cuisines on both weekdays and weekends. A small set of restaurants carries the platform.

**A feedback blind spot.** About **39% of orders (736) have no rating at all.** That's a huge chunk of the customer experience the company simply can't see — the single biggest data-quality issue surfaced by the analysis.

**Order values skew high.** **71% of orders cost more than $20**, and the cost distribution is right-skewed and arguably bimodal — consistent with two order types: small individual orders and larger group orders.

**Delivery is mostly fine, with a weekday problem.** Mean delivery time is ~24 minutes and only **11% of orders exceed 60 minutes** end-to-end. But **weekday deliveries run slower than weekends** (roughly 28 vs. 22 min median) — counterintuitive, and worth operational attention. Lower-rated (3-star) orders also tend to have longer prep/delivery times, hinting that speed drives satisfaction.

**Revenue picture.** Applying the platform's commission structure (25% on orders over $20, 15% on smaller qualifying orders) nets roughly **$6,167** across all orders in the sample.

## Business Recommendations

- **Close the ratings gap first.** With ~39% of orders unrated, add a post-delivery rating prompt or small incentive. Better feedback coverage makes every other analysis more reliable.
- **Run the promotion on proven performers.** Four restaurants meet the "50+ ratings and average rating above 4" bar — Shake Shack, The Meatball Shop, Blue Ribbon Sushi, and Blue Ribbon Fried Chicken — a low-risk, high-visibility promo group.
- **Investigate weekday delivery lag.** Slower weekday times correlate with lower ratings; identify whether it's staffing, traffic, or specific restaurants and fix the root cause.
- **Reward top customers.** The three most frequent customers are clear loyalty-program candidates.
- **Support underperforming cuisines.** Cuisines with low ratings and high uncertainty (few reviews) need either quality attention or more feedback volume before drawing conclusions.

## Repository

```
├── README.md
│── foodhub_data_analysis.ipynb   # data checks → univariate → multivariate → business Q&A
└── assets/                       # distribution and comparison charts
```

---

*Data analysis project — MIT Applied AI & Data Science (Foundations for Data Science). Built by Fuad Ahmadov.*
