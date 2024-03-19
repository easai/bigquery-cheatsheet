BigQuery: Summary
=========

## Contents

  - [00 Not implemented](summary.md#00-not-implemented)
  - [ARRAY_AGG](summary.md#array_agg)
  - [ARRAY_CONCAT](summary.md#array_concat)
  - [ARRAY_TO_STRING](summary.md#array_to_string)
  - [CAST](summary.md#cast)
  - [Confidence Interval](summary.md#confidence-interval)
  - [COUNTIF](summary.md#countif)
  - [DATE_SUB](summary.md#date_sub)
  - [DATE_TRUNC](summary.md#date_trunc)
  - [FORMAT_DATE](summary.md#format_date)
  - [LAG](summary.md#lag)
  - [Median](summary.md#median)
  - [REGEXP_CONTAINS](summary.md#regexp_contains)


## 00 Not implemented

- ARRAY_IS_DISTINCT
- ARRAY_INCLUDES_ANY
- ARRAY_MAX
- ARRAY_MIN
- ARRAY_CONCAT_AGG
- ARRAY_FILTER
- ARRAY_INCLUDES

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

## ARRAY_CONCAT

Concatenates arrays.<br />
Example:

```sql
SELECT
  ARRAY_CONCAT((SELECT ...), (SELECT ...)) 
```
Source: [name-e-a](https://github.com/easai/name-e-a/blob/main/script.sql)

## ARRAY_TO_STRING

Joins elements with arg and creates a string.<br />
Example:

```sql
SELECT
  ARRAY_TO_STRING([state_abbreviation, name], '-') AS airport_info
```
Source: [highest-airport](https://github.com/easai/highest-airport/blob/main/script.sql)


## CAST

Converts the data type.<br />
Example:

```sql
CAST(id AS INT64)
```

## Confidence Interval

Calculates 95% confidence interval.<br />
Example:

```sql
gdm.sample_average + (1.96 * gdm.pop_stddev / SQRT(sc.species_count)) AS upper_bound,
gdm.sample_average - (1.96 * gdm.pop_stddev / SQRT(sc.species_count)) AS lower_bound
```
Source: [confidence-interval](https://github.com/easai/confidence-interval/blob/main/script.sql)

## COUNTIF

Counts if true.<br />
Example:

```sql
COUNTIF(tip_threshold_exceeded = 1) AS tip_threshold_exceeded_count
```
Source: [fare_amount](https://github.com/easai/fare-amount/blob/main/script.sql)

## DATE_SUB

Subtract the specified amount from a date.<br />
Example:

```sql
WHERE
  i.established_date >= DATE_SUB (CURRENT_DATE(), INTERVAL 20 YEAR)
```
Source: [fdic-bank-list](https://github.com/easai/fdic-bank-list/blob/main/script.sql)



## DATE_TRUNC

Extract the specified component from a date.<br />
Example:

```sql
SELECT
  DATE_TRUNC (report_date, MONTH) AS report_month
```
Source: [salmonella](https://github.com/easai/salmonella/blob/main/script.sql)

## FORMAT_DATE

Formats the date.<br />
Example:

```sql
SELECT
  FORMAT_DATE ("%b %Y", report_month) AS formatted_month
```
Source: [salmonella](https://github.com/easai/salmonella/blob/main/script.sql)

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

## Median

Calculates the median value.<br />
Example:

```sql
SELECT
  PERCENTILE_CONT(passenger_count, 0.5) OVER () AS median_passenger_count
```
Source: [median-passenger-count](https://github.com/easai/median-passenger-count/blob/main/script.sql)

## REGEXP_CONTAINS

True if the field matches with the regex expression.<br />
Example:

```sql
 REGEXP_CONTAINS(c.text, r"(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)")
 ```
Source: [stackoverflow-ip-address/script.sql](https://github.com/easai/stackoverflow-ip-address/blob/main/script.sql)

