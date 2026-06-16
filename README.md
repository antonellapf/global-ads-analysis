# Global Ads Analysis
## Project Overview

In this project, I analyze digital advertising performance across Google Ads, Meta Ads, and TikTok Ads using BigQuery SQL and Power BI. The goal is to evaluate marketing efficiency and identify opportunities to improve Return on Ad Spend (ROAS), conversions, and overall campaign performance across different industries, countries, and campaign types.
Dataset Source: Public marketing performance dataset from Kaggle.

## Analysis Approach
Before transforming the data and building dashboards, it is important to understand the business context and define the questions the data can answer.

### Business Questions

I am focusing on five key business questions:
1. Which advertising platform generates the highest Return on Ad Spend (ROAS)?
2. Which industries generate the strongest marketing performance?
3. How does advertising spend impact revenue and ROAS?
4. Which campaign types are most effective?
5. Which countries represent the strongest marketing opportunities?

## Exploring the Data
Columns:
Date, Platform, Campaign Type, Industry, Country, Impressions, Clicks, CTR, CPC, Ad Spend, Conversions, CPA, Revenue, ROAS

```sql
-- Check for missing values across all columns
SELECT
  COUNTIF(date IS NULL) AS null_date,
  COUNTIF(platform IS NULL) AS null_platform,
  COUNTIF(campaign_type IS NULL) AS null_campaign_type,
  COUNTIF(industry IS NULL) AS null_industry,
  COUNTIF(country IS NULL) AS null_country,

  COUNTIF(impressions IS NULL) AS null_impressions,
  COUNTIF(clicks IS NULL) AS null_clicks,
  COUNTIF(CTR IS NULL) AS null_ctr,
  COUNTIF(CPC IS NULL) AS null_cpc,
  COUNTIF(ad_spend IS NULL) AS null_ad_spend,

  COUNTIF(conversions IS NULL) AS null_conversions,
  COUNTIF(CPA IS NULL) AS null_cpa,
  COUNTIF(revenue IS NULL) AS null_revenue,
  COUNTIF(ROAS IS NULL) AS null_roas

FROM `global-ads-analysis.marketing_analytics.raw_campaign_data`;
```
### Findings
No missing values were identified across any of the dataset columns. As a result, no imputation or data cleansing was required prior to analysis.

### Duplicate Records Check
```sql
-- Data quality validation: null value assessment
SELECT
  date,
  platform,
  campaign_type,
  industry,
  country,
  COUNT(*) AS rows_found
FROM `global-ads-analysis.marketing_analytics.raw_campaign_data`
GROUP BY
  date,
  platform,
  campaign_type,
  industry,
  country
HAVING COUNT(*) > 1
ORDER BY rows_found DESC;
```
### Data Quality Conclusion

The dataset passed all initial quality checks.
- No missing values were identified.
- No fully duplicated records were identified.
- Data types were successfully imported and validated.

The dataset is suitable for further exploratory and business analysis.


