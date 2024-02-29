BigQuery: Summary
================================

## Contents

  - [CAST](#cast)
  - [REGEXP_CONTAINS](#regexp_contains)
  - [LAG](#lag)
  - [ARRAY_AGG](#array_agg)


## CAST

Convert the data type.<br />
Example:

```sql
CAST(id as INT64)
```

## REGEXP_CONTAINS

True if the field matches with the regex expression.<br />
Example:

```sql
 REGEXP_CONTAINS(c.text, r"(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)")
 ```

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

## ARRAY_AGG

Returns an array.<br />
Example:

```sql
ARRAY_AGG(`hash` ORDER BY size DESC LIMIT 1)[OFFSET(0)] AS largest_block_hash
 ```


