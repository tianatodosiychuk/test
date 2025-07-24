# Will the Customer Accept the Coupon?

**Repository:** https://github.com/your-username/coupon-acceptance-analysis  
**Notebook:** `analysis.ipynb` → EDA, visualizations, statistical tests, key recommendations  

---

## 🚀 TL;DR

- **Coffee-house coupons:** 65 % accepted at 10 AM by 1–8×/mo visitors → push morning & afternoon.  
- **Bar coupons:** 70 % accepted by > 3×/mo bar-goers aged 26–40 when no kids in car.  
- **Restaurant coupons (under $20):** 2-hr expiry underperforms in evening traffic by 30 % → extend to 1 day.  

---

## Context

Imagine you’re driving through town and a coupon pops up on your phone for a nearby venue.  
- Would you detour right away?  
- Would you save it for later?  
- Or ignore it entirely?  

Scenarios vary by coupon type (coffee house, bar, inexpensive or expensive restaurant, carry-out), time of day, weather, passenger, and expiration. We ask: **once delivered, what factors drive acceptance?**

---

## Overview

**Goal:** Use visualizations and probability distributions to distinguish between drivers who accept (`Y=1`) versus reject (`Y=0`) a delivered coupon.

---

## Data & Attributes

**Source:** UCI Machine Learning Repository (Amazon Mechanical Turk survey)  
**Responses:**  
- “Right away” or “Later before expiration” → `Y = 1`  
- “No, I do not want the coupon” → `Y = 0`  

### User Attributes  
- **Gender:** male, female  
- **Age:** <21, 21–25, 26–30, …  
- **Marital Status:** single, married partner, unmarried partner, widowed  
- **Children:** 0, 1, >1  
- **Education:** high school, associate, bachelor, graduate  
- **Occupation:** e.g. architecture & engineering, farming/fishing/forestry, business & financial, …  
- **Annual Income:** <12 500, 12 500–24 999, 25 000–37 499, …  
- **Visit Frequencies:** bar, coffee house, cheap restaurant, takeaway (0, <1, 1–3, 4–8, >8 per month)  

### Contextual Attributes  
- **Destination:** home, work, no urgent destination  
- **Proximity:** time to venue (in minutes)  
- **Weather:** sunny, rainy, snowy  
- **Temperature:** 30 °F, 55 °F, 80 °F  
- **Time of Day:** 10 AM, 2 PM, 6 PM  
- **Passenger:** alone, partner, kids, friends  
- **Expiration:** 2 hours, 1 day  

---

## Key Findings

### 1. Less Expensive Restaurants (< \$20)  
- **Insight:** Moderate restaurant-goers (1–3×/mo) accept ~50 % around **lunch** (12 PM), especially when alone or with a partner. Acceptance drops below 35 % when children are present.  
- **Recommendation:** Deliver lunch-hour restaurant coupons (under \$20) to 1–3×/mo diners traveling alone/with partner.

### 2. Coffee Houses  
- **Insight:** 1–8×/mo coffee visitors accept at 65 % around **10 AM**, peaking again at 2 PM. Younger adults (21–30) and professionals show strongest uptake.  
- **Recommendation:** Push coffee-house coupons at 10 AM & 2 PM to frequent visitors; tailor messaging by age segment.

### 3. Carry-out & Takeaway  
- **Insight:** Frequent takeaway customers (4–8×/mo) accept ~60 % when **destination=Home** at **6 PM**. Acceptance falls below 30 % if children are onboard.  
- **Recommendation:** Deliver dinner-time takeaway coupons when destination is Home, targeting 4–8×/mo customers.

### 4. Bars  
- **Insight:** >3×/mo bar-goers aged 26+ accept ~70 % when **no kids** in car. Occupation in Farming/Fishing/Forestry shows lower acceptance, suggesting lifestyle fit matters.  
- **Recommendation:** Target frequent bar-goers aged 26+ with bar coupons—avoid families with children.

### 5. More Expensive Restaurants (\$20–\$50)  
- **Insight:** Overall acceptance ~35 %, rising to ~55 % among high-income (> \$75 K) drivers at **6 PM**, alone or with partner. 2-hr expiry reduces uptake by 20 %.  
- **Recommendation:** Offer 1-day expiration for high-income segments during dinner hours; personalize toward partner/solo trips.

---

## Consolidated Recommendations

- **Timing:**  
  - Coffee: 10 AM & 2 PM  
  - Lunch restaurants: 11 AM–1 PM  
  - Dinner venues & takeaway: 5 PM–7 PM  
- **Segments:**  
  - Frequent venue-goers (1–8×/mo)  
  - Age 21–40 for coffee & bars  
  - High-income for expensive restaurants  
- **Context:**  
  - Avoid families with children for bars & takeaway  
  - Extend short expirations (2 hr → 1 day) when traffic delays are likely  

---

## Next Steps

1. **Predictive Modeling:** Train logistic regression / random forest on these features to predict acceptance (`Y=1`).  
2. **A/B Testing:** Deploy segmented coupon pushes in-app and measure lift in real campaigns.  
3. **Feature Engineering:** Create interaction features (e.g. `time_of_day × passenger`, `visit_frequency × income`).  

---


