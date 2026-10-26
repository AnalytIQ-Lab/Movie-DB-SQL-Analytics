# Executive Summary

## Overview

This report contains 8 findings that passed the register completeness gate. 0 additional insight(s) remain pending or not assessed.

## Key Business Findings

### Portfolio

**Finding:** Drama is the most represented genre in the catalogue, associated with 2,297 distinct movies.

**Evidence:** Movie Master contains 4,803 distinct movies. 4,775 have a nonblank genre field. The leading genre is associated with 2,297 movies (47.8% of all movies).

**Business implication:** Genre counts describe catalogue coverage; they do not by themselves establish demand or profitability.

**Recommended action:** Use genre coverage to describe the catalogue, then compare financial distributions using the distinct movie–genre mapping.

**Initial priority:** Medium

**Confidence:** High

**Limitation:** Movies can belong to multiple genres, and missing genre labels limit coverage.

### Financial Performance

**Finding:** 2,438 of 3,766 movies with valid financial records are profitable (64.7%).

**Evidence:** Valid population: budget > 0 and recorded finite revenue >= 0. Within this population: 2,438 profitable, 1,326 loss-making, and 2 break-even. Median ROI is 86.8%. 1,037 of 4,803 movies are excluded from this financial comparison.

**Business implication:** This is a simplified budget-versus-revenue measure, not a complete accounting profit measure.

**Recommended action:** Use the valid-record population for profitability and ROI reporting; review excluded records before using these metrics for investment decisions.

**Initial priority:** High

**Confidence:** High

**Limitation:** Budget and revenue may omit marketing, distribution, financing, tax, and other costs. Recorded revenue may not equal total lifetime revenue.

### Investment Efficiency

**Finding:** Budget and revenue have a Pearson correlation of 0.710 across valid financial records.

**Evidence:** Pearson r = 0.710; n = 3,766 movies with positive budgets and valid recorded revenue.

**Business implication:** The observed association can help prioritize deeper segmentation, but it does not show that higher budgets cause higher revenue.

**Recommended action:** Compare budget bands, release periods, and ROI distributions before drawing investment conclusions.

**Initial priority:** High

**Confidence:** Moderate

**Limitation:** Pearson correlation can be influenced by extreme values and does not control for genre, release year, franchise, or marketing spend.

### Genre Strategy

**Finding:** Animation has the highest median ROI among genres with at least 20 valid financial movies.

**Evidence:** Eligible genre sample size threshold: 20 valid movies. Animation: 208 valid movies; median ROI 129.9%; median revenue 149,725,490.

**Business implication:** Genre-level distributions can inform further portfolio review but are not evidence that genre membership causes financial performance.

**Recommended action:** Review median ROI alongside sample size, median revenue, and median profit before using genre results in planning.

**Initial priority:** High

**Confidence:** Moderate

**Limitation:** Movies may belong to multiple genres; comparisons overlap. ROI is sensitive to very small budgets and recorded revenue may be incomplete.

### Popularity

**Finding:** Popularity and recorded revenue have a Pearson correlation of 0.645.

**Evidence:** Pearson r = 0.645; n = 4,803 movies with finite popularity and recorded non-negative revenue.

**Business implication:** Popularity is associated with revenue in this dataset, but the relationship is not causal and may reflect other factors.

**Recommended action:** Use popularity as one descriptive signal alongside budget, release period, genre, and franchise status—not as a standalone revenue forecast.

**Initial priority:** Medium

**Confidence:** Moderate

**Limitation:** Popularity score definition and timing may be unclear; revenue and popularity can be skewed by extreme observations.

### Production

**Finding:** Top production-company association: Warner Bros. (319 movies; 7.2% of movies with a recorded company); Top production-country association: United States of America (3,956 movies; 85.5% of movies with a recorded country).

**Evidence:** Counts are distinct movies associated with each comma-separated company/country. Each percentage denominator is the number of movies with a nonblank value for that field.

**Business implication:** These counts describe production associations, not exclusive market shares or attributable revenue.

**Recommended action:** Review the distribution of distinct movies by production company and country, while treating multi-company and multi-country records as overlapping categories.

**Initial priority:** Medium

**Confidence:** High

**Limitation:** A movie can list multiple production companies and countries; missing labels affect denominators.

### Artist Participation

**Finding:** Samuel L. Jackson has the highest recorded participation count, with 67 distinct movies.

**Evidence:** The participation table represents 54,588 distinct artists. Counts are based on distinct artist–movie pairs, not raw artist–character rows.

**Business implication:** Participation counts can describe catalogue coverage but do not measure an artist's commercial contribution.

**Recommended action:** Use the deduplicated artist–movie table to review participation and collaboration patterns; do not attribute full movie revenue to artists.

**Initial priority:** Low

**Confidence:** High

**Limitation:** Credits may be incomplete, and repeated characters or credits can still reflect source-data conventions.

### Data Quality

**Finding:** 4,803 movie rows and 4,803 distinct Movie_ID values; 0 duplicate Movie_ID values; 1,037 records without a valid positive budget; 0 records without valid recorded non-negative revenue; 1,037 records excluded from financial analysis; 1 missing release dates; 28 missing genre values; 351 missing production-company values; 174 missing production-country values.

**Evidence:** Financial-analysis eligibility is 78.4% of Movie Master records (3,766 of 4,803).

**Business implication:** Incomplete or invalid inputs change the population used for financial KPIs and can bias comparisons if exclusions are ignored.

**Recommended action:** Publish metric denominators and exclusion counts alongside financial results; investigate invalid budget and revenue records before relying on the KPIs.

**Initial priority:** High

**Confidence:** High

**Limitation:** This is a current-state completeness check; it does not establish why values are missing or whether the source values are correct.

## Reporting cautions

- Profit is defined here as recorded revenue minus recorded budget for the valid financial population only.
- ROI is simplified profit divided by positive budget; it is not a complete investment return measure.
- Correlation describes association, not causation.
- Genre, production-company, and production-country categories overlap; category counts must not be summed as exclusive totals.
- Weighted prioritization remains pending until impact, urgency, and implementation effort are assessed.

## Pending insights

No insights are pending the register completeness gate.