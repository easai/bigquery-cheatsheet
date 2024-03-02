BigQuery: Summary
================================

## Contents

  - [CAST](#cast)
  - [COUNTIF](#countif)
  - [REGEXP_CONTAINS](#regexp_contains)
  - [LAG](#lag)
  - [ARRAY_AGG](#array_agg)
  - [Confidence Interval](#confidence-interval)
  - [ARRAY_CONCAT](#array_concat)

## CAST

Converts the data type.<br />
Example:

```sql
CAST(id AS INT64)
```

## COUNTIF

Counts if true.<br />
Example:

```sql
COUNTIF(tip_threshold_exceeded = 1) AS tip_threshold_exceeded_count
```
Source: [fare_amount](https://github.com/easai/fare-amount/blob/main/script.sql)

## REGEXP_CONTAINS

True if the field matches with the regex expression.<br />
Example:

```sql
 REGEXP_CONTAINS(c.text, r"(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)")
 ```
Source: [stackoverflow-ip-address/script.sql](https://github.com/easai/stackoverflow-ip-address/blob/main/script.sql)

## LAG

Returns the field value of the previous row.<br />
Example:

```sql
  CASE 
    WHEN mbs.avg_weight > LAG(mbs.avg_weight) OVER (ORDER BY mbs.timestamp_month)
    THEN 'Increased'
    WHEN mbs.avg_weight < LAG(mbs.avg_weight) OVER (ORDER BY mbs.timestamp_month)
    THEN 'Decreased'
    ELSE 'Stable'
  END AS avg_weight_trend
 ```
Source: [hash-block](https://github.com/easai/hash-block/blob/main/script.sql)

## ARRAY_AGG

Creates an array.<br />
Example:

```sql
SELECT
    ARRAY_AGG (name)
FROM
    (SELECT ...)
```
Source: [name-e-a](https://github.com/easai/name-e-a/blob/main/script.sql)

```sql
ARRAY_AGG(`hash` ORDER BY size DESC LIMIT 1)[OFFSET(0)] AS largest_block_hash
 ```
Source: [hash-block](https://github.com/easai/hash-block/blob/main/script.sql)

## Confidence Interval

Calculates 95% confidence interval.<br />
Example:

```sql
gdm.sample_average + (1.96 * gdm.pop_stddev / SQRT(sc.species_count)) AS upper_bound,
gdm.sample_average - (1.96 * gdm.pop_stddev / SQRT(sc.species_count)) AS lower_bound
```
Source: [confidence-interval](https://github.com/easai/confidence-interval/blob/main/script.sql)

## ARRAY_CONCAT

Concatenates arrays.<br />
Example:

```sql
SELECT
  ARRAY_CONCAT((SELECT ...), (SELECT ...)) 
```
Source: [name-e-a](https://github.com/easai/name-e-a/blob/main/script.sql)


