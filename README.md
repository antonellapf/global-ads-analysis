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

### Duplicate Records
```sql
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


