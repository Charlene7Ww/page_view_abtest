# A/B Testing – E-commerce Product Page Redesign
## 📘 Project Overview

This project analyzes an A/B test conducted by a mid-sized e-commerce company selling home and lifestyle products online.
The goal was to determine whether the new product detail page (PDP) design improves user engagement and purchase conversion compared to the current layout.

## 🏢 Business Context
### Company Background

The company operates an online platform offering home and lifestyle products.
The marketing team recently launched a redesigned PDP aimed at enhancing visual appeal, usability, and conversion.

### Variant	Description
Group A (Control)	Current layout with standard product info and basic structure
Group B (Treatment)	New design featuring larger images, top-positioned customer reviews, and AI-based product recommendations

- Randomization Unit: Individual user (User ID)

- Duration: 2 weeks

- Primary Metric: Conversion (purchase made: Yes/No)

- Secondary Metrics: Page Views, Time Spent on Site

- Segments: Device (Mobile/Desktop) and Location (England, Scotland, Wales, Northern Ireland)

## 🧹 1. Data Cleaning & Preparation

- Dataset: ab_testing.csv

- 5,000 observations

- No missing or duplicate user_id

- Converted categorical “Conversion” → binary (Yes = 1, No = 0)

### Sample columns:

user_id	group	page_views	time_spent	conversion	device	location
14292	B	3	424	0	Mobile	Northern Ireland

### Split check (SRM test):
A: 50.38% B: 49.62% → ✅ Balanced randomization

## 📊 2. Statistical Testing
### 2.1 Conversion Rate Test (Z-test)
Metric	A (Control)	B (Treatment)	Result
Conversion Rate	5.4%	14.1%	z = 10.00, p < 0.001 ✅

Interpretation:
The new design (Group B) significantly increased conversion — a statistically significant improvement.

95% CI (Group B): [12.7%, 15.4%]

2.2 Time Spent (t-test)
Metric	A	B	p-value
Avg Time Spent (sec)	241.7	243.3	0.64 ❌

No significant difference — new page does not increase time spent, implying a faster or more efficient browsing experience.

2.3 Page Views (t-test)
Metric	A	B	p-value
Avg Page Views	7.58	7.49	0.44 ❌

No significant change in browsing depth — engagement remains stable.

📈 3. Effect Size & Business Impact
Relative Lift
𝐿
𝑖
𝑓
𝑡
=
𝐵
−
𝐴
𝐴
=
156.6
%
Lift=
A
B−A
	​

=156.6%

➡️ Conversion increased by ~157%.

Segment-Level Analysis
By Device
Device	A	B	Lift (%)
Desktop	5.9%	13.9%	+137%
Mobile	4.9%	14.2%	+188%

🔍 The uplift is strongest among mobile users, suggesting the new PDP is particularly effective for smaller screens.

By Location
Location	A	B	Lift (%)
England	6.9%	14.7%	+112%
Northern Ireland	5.0%	11.5%	+127%
Scotland	4.9%	15.1%	+206%
Wales	4.8%	15.1%	+217%

🔍 Scotland and Wales show the highest improvement, hinting at regional differences in responsiveness to visual or UX enhancements.

🎨 4. Visualization Highlights

Overall Conversion Rate Bar Chart: shows clear uplift for Group B.

Conversion Lift by Device: Mobile > Desktop.

Conversion Lift by Location: Strongest in Wales and Scotland.

Heatmap (Device × Location): confirms combined lift patterns.

Page Views & Time Spent Bars: no negative impact on engagement.

💡 5. Key Insights
Area	Finding	Business Meaning
Conversion	+157% lift, p<0.001	Redesign directly drives higher purchases
Time Spent	No significant change	More efficient shopping experience
Device	Mobile +188% lift	Optimize rollout for mobile-first experience
Location	Wales & Scotland +200%+	Regionally strong impact — tailor localization/ads
🧭 6. Recommendations

✅ Roll out the new product page (Group B) across all users.

📱 Prioritize mobile optimization — largest incremental gain.

🌍 Investigate regional UX preferences (especially Scotland/Wales).

🔄 Continue A/B testing for personalization modules (AI recommendations, review placements).

🧮 Monitor post-launch metrics for sustained performance (conversion stability, bounce rate, checkout completion).

🛠️ 7. Tech Stack

Python: pandas, scipy, statsmodels, seaborn, matplotlib

Statistical Tests: Proportion Z-test, Welch’s t-test

Visualization: Matplotlib & Seaborn

Environment: Jupyter Notebook / Anaconda

📑 8. Summary

Result:
The new product page layout (Group B) significantly increased conversions (+157% overall, p < 0.001) without hurting engagement.
The effect is especially strong on mobile and in Wales & Scotland, indicating both design effectiveness and possible demographic influence.

Business Impact:
The redesign is a clear success — expected to increase total sales and improve user experience efficiency.
