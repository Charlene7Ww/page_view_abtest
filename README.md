# A/B Testing – E-commerce Product Page Redesign

## 1. Project Overview
This project analyzes an A/B test conducted by a mid-sized e-commerce company selling home and lifestyle products online.  
The goal was to determine whether the new product detail page (PDP) design improves user engagement and purchase conversion compared to the existing layout.

## 2. Business Context

**Company Background**  
The company operates an online platform offering home and lifestyle products.  
The marketing team recently launched a redesigned PDP aimed at improving visual appeal, usability, and conversion.

| Variant | Description |
|----------|--------------|
| Group A (Control) | Current layout with standard product info and minimal structure |
| Group B (Treatment) | New design featuring larger images, top-positioned reviews, and AI-based product recommendations |

- Randomization Unit: Individual user (User ID)  
- Duration: Two weeks  
- Primary Metric: Conversion (purchase made: Yes/No)  
- Secondary Metrics: Page Views, Time Spent on Site  
- Segments: Device (Mobile/Desktop), Location (England, Scotland, Wales, Northern Ireland)

## 3. Data Cleaning & Preparation

**Dataset:** `ab_testing.csv`  
- 5,000 rows, 7 columns  
- No missing or duplicate `user_id`  
- "Conversion" converted to binary (Yes=1, No=0)

| user_id | group | page_views | time_spent | conversion | device | location |
|----------|--------|------------|-------------|-------------|----------|-----------|
| 14292 | B | 3 | 424 | 0 | Mobile | Northern Ireland |
| 11682 | A | 9 | 342 | 0 | Mobile | Scotland |

**Split check (Sample Ratio Mismatch test):**  
A: 50.38% B: 49.62% → Balanced randomization ✅

## 4. Statistical Testing

### 4.1 Conversion Rate Test (Z-test)

| Metric | A (Control) | B (Treatment) | Result |
|---------|--------------|---------------|--------|
| Conversion Rate | 5.4% | 14.1% | z = 10.00, p < 0.001 (Significant) |

**Interpretation:**  
The new design (Group B) significantly increased conversion rates.  
95% Confidence Interval for Group B: (12.7%, 15.4%)

### 4.2 Time Spent (t-test)

| Metric | A | B | p-value |
|---------|---|---|----------|
| Avg Time Spent (seconds) | 241.7 | 243.3 | 0.64 (Not significant) |

No significant difference – the new page does not increase time spent, suggesting users can make purchase decisions more efficiently.

### 4.3 Page Views (t-test)

| Metric | A | B | p-value |
|---------|---|---|----------|
| Avg Page Views | 7.58 | 7.49 | 0.44 (Not significant) |

Browsing depth remains stable.

## 5. Effect Size & Business Impact

**Relative Lift:**

Lift = (B - A) / A = 156.6%

Conversion increased by approximately **+157%** overall.

### Segment Analysis

#### By Device

| Device | A | B | Lift (%) |
|---------|---|---|-----------|
| Desktop | 5.9% | 13.9% | +137% |
| Mobile | 4.9% | 14.2% | +188% |

Mobile users showed stronger uplift, indicating the redesign performs best on smaller screens.

#### By Location

| Location | A | B | Lift (%) |
|-----------|---|---|-----------|
| England | 6.9% | 14.7% | +112% |
| Northern Ireland | 5.0% | 11.5% | +127% |
| Scotland | 4.9% | 15.1% | +206% |
| Wales | 4.8% | 15.1% | +217% |

Strongest improvements observed in **Wales** and **Scotland**, indicating possible regional UX sensitivity.

## 6. Visualization Summary

- Overall Conversion Rate: Group B significantly higher than A.  
- Conversion Lift by Device: Mobile > Desktop.  
- Conversion Lift by Location: Highest in Wales and Scotland.  
- Time Spent & Page Views: No significant change.  
- Heatmap (Device × Location): Lift patterns consistent with device and region.

![image-20251022135328868](/Users/charlene2110/Library/Application Support/typora-user-images/image-20251022135328868.png)

## 7. Key Insights

| Area | Finding | Business Interpretation |
|------|----------|--------------------------|
| Conversion | +157% lift, p < 0.001 | Redesign directly drives more purchases |
| Time Spent | No significant change | Users shop faster, improved UX |
| Device | Mobile +188% lift | Prioritize mobile-first optimization |
| Location | Wales & Scotland +200%+ | Regional variation in user response |

---

## 8. Recommendations

1. Roll out the **new product page (Group B)** to all users.  
2. Prioritize **mobile UX improvements** for continued optimization.  
3. Investigate **regional user behavior** (Scotland & Wales) for targeted marketing.  
4. Continue **iterative A/B testing** on recommendation modules and layout variations.  
5. Monitor **post-launch metrics** (conversion, bounce rate, checkout completion) to confirm sustained performance.

---

## 9. Tech Stack

| Component | Tool / Library |
|------------|----------------|
| Data Processing | pandas |
| Statistical Tests | scipy, statsmodels |
| Visualization | matplotlib, seaborn |

## 10. Summary

The A/B test demonstrated that the **new PDP design (Group B)** significantly increased conversion rates (+157%) without reducing user engagement.  
The strongest uplift occurred among **mobile users** and in **Wales and Scotland**.  

**Conclusion:**  
The redesign should be rolled out site-wide, with a focus on mobile and regional optimization strategies.  
This experiment serves as a successful case of data-driven UX validation for e-commerce growth.
