# 📊 Employee Engagement & Perception Gap Analysis

## Objective

In this project, I designed and implemented an end-to-end Business Intelligence solution in IBM Cognos Analytics to evaluate employee survey responses across Pierce County, WA.

1. Extracted and cleaned raw employee engagement survey data using Cognos Data Modules.
2. Transformed text-based Likert responses into numeric float values (`1.0` - `4.0` scale) while filtering out invalid records ($0$ / N/A responses) using `CAST` and `CASE` functions.
3. Modeled categorical dimensions by grouping 20+ granular operational units into 4 broad functional department groups.
4. Developed an interactive executive dashboard featuring a sentiment driver heatmap, cross-departmental slicers, and role divergence tracking.

As this is a Business Intelligence and Data Modeling project, my emphasis is primarily on the analytics architecture, data transformation logic, and executive-level dashboard visualization.

The sections below explain additional details on the dataset, methodologies, and business insights.

---

## Table of Content

- [Dataset Used](#dataset-used)
- [Recommended Business Analysis](#recommended-business-analysis)
- [Technologies Used](#technologies-used)
- [Data Modeling & Transformation](#data-modeling--transformation)
- [Dashboard Screenshots](#dashboard-screenshots)
- [Key Findings & Actionable Recommendations](#key-findings--actionable-recommendations)

---

## Dataset Used

* **Source:** Pierce County, WA (Public Domain)
* **Domain:** HR Analytics & Employee Sentiment
* **Structure:** Entity-Attribute-Value (EAV) Survey Data Model
* **Volume:** 14,500+ completed survey response records across 25 fields

---

## Recommended Business Analysis

This project specifically resolves three primary business questions:

* **Question Driver Analysis:** Which survey questions and engagement drivers did respondents agree with or disagree with most?
* **Hierarchy & Departmental Trends:** Are there clear patterns, sentiment trends, or perception gaps between management roles (`Directors`, `Managers`) and frontline `Staff` across business units?
* **Actionable Next Steps:** As an employer, what strategic steps should be taken to improve employee retention and satisfaction based on driver divergence?

---

## Technologies Used

* **BI Platform:** IBM Cognos Analytics
* **Data Transformation:** IBM Cognos Data Modules (Custom Calculations, Type Casting, Aggregations)
* **Querying:** Custom SQL Expression Logic (`CASE` / `CAST`)

---

## Data Modeling & Transformation

To calculate weighted averages across survey questions, custom calculated fields were created within the Data Module:

* **Handling Nulls & Non-Numeric Responses:**
```sql
CASE 
  WHEN [Response_Text] IN ('1', '2', '3', '4') 
    THEN CAST([Response_Text] AS FLOAT)
  ELSE NULL 
END
