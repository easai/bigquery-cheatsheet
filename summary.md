BigQuery: Summary
================================

## Contents

  - [CAST](#cast)
  - [REGEXP_CONTAINS](#regexp_contains)
  - [LAG](#lag)
  - [ARRAY_AGG](#array_agg)


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
Source: (fare_amount)[https://github.com/easai/fare-amount]

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
Source: [hash-block](https://github.com/easai/hash-block)

## ARRAY_AGG

Returns an array.<br />
Example:

```sql
ARRAY_AGG(`hash` ORDER BY size DESC LIMIT 1)[OFFSET(0)] AS largest_block_hash
 ```
Source: [hash-block](https://github.com/easai/hash-block)


