
# Power-bi-project
# E-Commerce Customer Segmentation & Retention Analytics (Power BI)

## 📌 Project Overview
As an aspiring data analyst, I wanted to build an end-to-end business intelligence project that goes beyond basic summary charts and tackles real-world commercial challenges:  **customer churn, behavioral segmentation, and revenue preservation**.

Using a dataset of **50,000 global e-commerce customer transactions**, I designed an interactive 3-page Power BI dashboard. The goal was to help retail leadership and retention marketing teams quickly identify high-value customer clusters, monitor satisfaction bottlenecks, and proactively target accounts before they abandon the platform.




1. **Revenue Generation Identification:** Which customer segments generate the bulk of the revenue, and which high-value accounts are currently slipping away?
2. **Behavioral Segmentation:** How are customers distributed across RFM (Recency, Frequency, Monetary) groups, and what separates one-time buyers from high-loyalty champions?
3.  **Retention Strategy**: What friction points (returns, complaints, low CSAT) trigger churn, and which specific high-spending accounts need immediate outreach?

---

## 🛠️ Tech Stack & Skills
- **BI Tool:** Power BI Desktop / Power BI Service
- **Data Transformation:** Power Query (M Language) for schema optimization, data cleaning, and deduplication
- **Analytical Calculations:** Custom DAX measures (`CALCULATE`, `FILTER`, `DISTINCTCOUNT`, `DIVIDE`, aggregations)
- **Data Modeling:** Star Schema design, explicit measures table organization
- **Visual Storytelling:** Custom KPI cards, conditional formatting heatmaps, top-N dynamic filtering, bookmark reset actions

---

## 📊 Dashboard Structure

<img width="1209" height="664" alt="Screenshot 2026-09-04 083930" src="https://github.com/user-attachments/assets/611486fd-dfd8-4e5d-afae-bee15ac38ac6" />

### Page 1: Executive Overview & Revenue Performance
- **Primary Focus:** High-level enterprise health and revenue channel performance.
- **Key KPIs:** Total Revenue ($2.51B), Total Customers (50K), Average Order Value ($505.37), Average CLV ($57.72K), and Total Purchases (4.97M).
- **Core Visuals:**
  - **Revenue by Customer Segment:** Donut chart highlighting Consumer accounts as the largest revenue driver (45.2% share).
  - **Category Performance:** Ranked horizontal bar chart identifying leading categories (Electronics, Fashion, Home & Kitchen).
  - **Channel vs. Payment Heatmap:** Matrix visual using gradient conditional formatting to highlight customer purchasing preferences across channels (Mobile App, Online, In-Store, Marketplace) and payment types.
  - **Top 10 Global Markets:** Column chart displaying top revenue-generating countries.

---
<img width="1339" height="747" alt="Screenshot 2026-09-04 084035" src="https://github.com/user-attachments/assets/da5dfdc6-f3f0-4d0c-a3cd-7c36fdd6e27d" />

### Page 2: Customer Segmentation & RFM Behavior
- **Primary Focus:** Behavioral grouping based on Recency, Frequency, and Monetary scores.
- **Key KPIs:** Champions Count (22,971), Champions Revenue ($1.75B), At-Risk Customer Count (5,463), and Average Tenure (59.7 months).
- **Core Visuals:**
  - **RFM Distribution Treemap:** Visualizing customer concentration across Champions, Loyal, Potential Loyalists, At Risk, and Need Attention categories.
  - **Recency vs. Spend Dynamics:** Clustered column chart showing the sharp contrast between active Champions (~16.7 recency days) and disengaged groups (>120 days).
  - **Loyalty Tier Cross-Analysis:** 100% stacked bar chart showing membership distribution (Diamond, Platinum, Gold, Silver, Bronze) across behavioral categories.
  - **Customer Activity Scatter Plot:** Highlighting spend vs. inactivity patterns across the entire user base.

---
<img width="1332" height="748" alt="Screenshot 2026-09-04 084112" src="https://github.com/user-attachments/assets/b9cf6aab-887a-4676-b07f-8cdbf1367179" />

### Page 3: Churn Risk & Retention Operations
 **Primary Focus:** Identifying retention bottlenecks and serving operational target lists to customer success teams.
**Key KPIs:** High Churn Risk Customers (2,702), Revenue at Risk ($122.12M), Average CSAT (3.01 / 5), and Average Complaints (7.0 per user).
 **Core Visuals:**
   **Churn Risk Breakdown:** Donut chart isolating accounts flagged in High and Very High risk categories.
   **Revenue at Risk by Segment:** Identifies that Consumer accounts carry the largest gross risk ($54.07M), while Enterprise and Small Business clients present high individual value exposure.
  - **Service Friction Analysis:** Charting the direct correlation between complaint counts, return frequency, and low customer satisfaction scores.
  - **Operational Retention Target Table:** A filtered, descending-spend table ranking the most critical at-risk accounts (e.g., spend > $190K, days inactive > 200) with color-coded churn risk indicators for targeted win-back campaigns.

---

## 📈 Key Insights & Recommendations
- **Champions Drive the Business:** Champions represent roughly 46% of the customer base but account for nearly **70% of total revenue ($1.75B)**. Retention programs must protect this tier above all else.
- **Actionable Revenue at Risk:** Over **$122M in historical sales** is tied to just 2,702 customers showing high disengagement signals. Re-engaging even 10% of this group preserves over $12M in recurring value.
- **Service Friction Impacts Retention:** Customers with satisfaction ratings below 3 consistently exhibit elevated return and complaint volumes, pointing to logistics and product onboarding as key operational fix areas.

---

## 🧮 Sample DAX Measures Used

```dax
// Total Revenue Measure
Total Revenue = SUM('E-commerce_Customer_Segmentation_2026'[total_spent_usd])

// Identifying High Risk Customers
High Churn Customers = 
CALCULATE(
    DISTINCTCOUNT('E-commerce_Customer_Segmentation_2026'[customer_id]),
    'E-commerce_Customer_Segmentation_2026'[churn_risk_category] IN {"High", "Very High"}
)

// Revenue at Risk Calculation
Revenue at Risk = 
CALCULATE(
    [Total Revenue],
    'E-commerce_Customer_Segmentation_2026'[churn_risk_category] IN {"High", "Very High"}
)

// Profit Margin %
Profit Margin % = 
DIVIDE(
    SUM('E-commerce_Customer_Segmentation_2026'[customer_profitability_usd]),
    [Total Revenue],
    0
)
🚀 How to Run This Project Locally
Download the .pbix report file from this repository.

Ensure you have the latest version of Power BI Desktop installed.

Open the .pbix file. (If prompted for the data source path, map the source file to your local copy of E-commerce_Customer_Segmentation_2026.csv).

Refresh the dataset to load visuals and slicers.

