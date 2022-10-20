---
title: Data aggregation
date: 2022-10-20
---

## Data aggregation
- **What is data aggregation (agg)?**
    - An action that collapses a set of values to a single value
    - Aggregation is also called summarization
- **Why data agg?**
    - Human brain are not capable of making sense of a large number of values
    - By data agg, we get digestible information that can support decision making
    - Example: how can you recognize one of your friend?
- **What are the trade-off?**
    - Cons: we lose the richness and many details of the original data
    - Pros: we gain digestible information that we can make sense of
- **How to do agg?**
    - We summarize data using summary statistics (or descriptive stats)
    - SQL provide use with summary function such as `COUNT`, `MIN`, `MAX`, `AVG`, ...
    - We can aggregate data on the entire table or by group (using `GROUP BY`)

## Aggregation on the entire column
- We collapse an entire column into a single summary stats
- **Syntax**
```sql
SELECT
    agg_func_1(col_name_1) AS summary_1,
    agg_func_2(col_name_2) AS summary_2,
    ...
FROM <tbl>
```

### Count
**Preview `Product`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
```

**Ex 1: count all rows in `Product`**
- `COUNT()` will count the number of **non-NULL** values only
```sql
-- You get 295 rows
USE adventureworks

SELECT COUNT(*)
FROM SalesLT.Product
```

**Ex 2: count only on `Weight` column of `Product`**
```sql
-- You get only 198 rows only
-- Because there are many rows with NULL Weight
USE adventureworks

SELECT COUNT(Product)
FROM SalesLT.Customer
```

### Count distinct
**Ex 1: count number of distinct (unique) colors from `Product`**
- Only count non-NULL values
```sql
-- You get 9
-- Note that COUNT is a function, so () are required
USE adventureworks

SELECT COUNT(DISTINCT Color)
FROM SalesLT.Product
```

- To verify, `SELECT DISTINCT` and manually count the result
```sql
USE adventureworks

SELECT DISTINCT Color
FROM SalesLT.Product
```

**Ex 2: count number of distinct pair `Color` and `Size`**
- For MySQL or PostgreSQL, counting distinct values of multiple columns is more natural
```sql
-- You will get 68
-- This works for MySQL and PostgreSQL, not SQL Server
-- That's why each variation of SQl is like a dialect
USE adventureworks

SELECT COUNT(DISTINCT Size, Color)
FROM SalesLT.Product
```

- For SQL Server (using T-SQL language), you cannot count distinct on multiple columns
- To do so, you have to concatenate those columns into a single one and then count distinct on that column
```sql
-- Note that Color + Size will return NULL 
-- if one of the two columns is NULL
USE adventureworks

SELECT COUNT(DISTINCT Color + Size)
FROM SalesLT.Product
```

### Sum
**Ex 1: compute the all-time total revenue from `SalesOrderDetail`**
```sql
USE adventureworks

SELECT 
    SUM(LineTotal) AS GrandTotal
FROM SalesLT.SalesOrderDetail
```

### Measures of locations
#### Motivation
- Often data are large (Ex: millions of rows), so looking at all data point to find insights is hopeless
- One way to make sense of the data is to look at the following characteristics
    - **Important locations:** min, max, top 25%, median, top 75%, top 99%, ...
        - Min, max: extreme locations
        - Median, average: central locations
        - Top `x%` (quantiles, percentiles): arbitrary locations
    - **The variation in the data:** variance, standard deviation, IQR, ...

#### Measures of central locations
- What are they?
    - They are summary stats that capture the typical values of the whole dataset
    - Example
        - You have to guess the height of a random American man
        - You know that the average height of American men is `1.75m`
        - Without further information, your best guess should be `1.75`
- Summary stats for measures of central location
    - Mean (average): common
    - Median: less common because computationally expensive
    - Mode: rarely used because computationally expensive and not so meaningful

**Ex 1: compute average list price and standard cost of all available products from `Product`
```sql
USE adventureworks

SELECT 
    AVG(ListPrice) AS avg_list_price,
    AVG(StandardCost) AS avg_std_cost
FROM SalesLT.Product
```

#### Measures of extreme locations
- These are smallest (minimum) and largest (maximum) values in the dataset

**Ex 1: Compute smallest and largest list price from `Product`**
```sql
USE adventureworks

SELECT 
    MIN(ListPrice) AS min_list_price,
    MAX(ListPrice) AS max_list_price
FROM SalesLT.Product
```

**Ex 2: from `SalesOrderHeader` table, compute the time range of the orders in the table**
```sql
USE adventureworks

SELECT 
    MIN(OrderDate) AS min_order_date,
    MAX(OrderDate) AS max_order_date
FROM SalesLT.SalesOrderHeader
```

#### Measures of arbitrary locations
- These include 
    - Quartiles: Q1, Q3
    - Percentile: 1%, 10%, 90%, 99%, ...
    - Quantiles: just percentiles expressed in decimal values from 0 to 1
- These measure are not covered in this course

### Measures of variation
#### Variance
- What is it?
    - It is the average of squared deviations from the center of the dataset (avg)
    - Formula for sample variance: $\frac{\Sigma_{i=1}^N(x_i - \bar{x})^2}{N-1}$
- Interpretation
    - Larger variance means data points spread out more
    - Smaller variance means data points are more similar and cluster around the mean
    - Not meaningful by itself, only meaningful when comparing between groups

#### Standard deviation
- What is it?
    - It is the square root of variance
- Why standard deviation?
    - Because it is in the same unit as that of the data -> easier to interpret

**Ex 1: compute the mean, variance, and standard deviation of list price of all products in `Product`**
```sql
USE adventureworks

SELECT 
    AVG(ListPrice) AS avg_list_price,
    VAR(ListPrice) AS var_list_price,
    STDEV(ListPrice) AS std_list_price
FROM SalesLT.Product
```

## Aggregation by group
- We have the same logic as previously
- But now, instead of a single summary stats for the entire column, we have a single summary stats for each unique group
- **Syntax**
```sql
SELECT
    -- List of columns to group by
    <agg_col_list>, 

    -- List of aggregations to compute
    agg_func_1(col_1) AS summary_1,
    agg_func_2(col_2) AS summary_2,
    ...
FROM <tbl>
GROUP BY <agg_col_list>
ORDER BY <agg_col_list> -- Optional
```

> **Tips**
> - Write `SELECT *`
> - Then `FROM <table_name>`
> - Then `GROUP BY <col_list>`
> - Then move back to `SELECT` part to write the aggregation expressions

**Ex 1: from `Address` table, count number of rows for each country**
```sql
USE adventureworks

SELECT 
    CountryRegion,
    COUNT(*)
FROM SalesLT.Address
GROUP BY CountryRegion
ORDER BY CountryRegion
```

**Ex 2: from `Address` table, count number of unique states/provinces for each country**
```sql
USE adventureworks

SELECT 
    CountryRegion,
    COUNT(DISTINCT StateProvince)
FROM SalesLT.Address
GROUP BY CountryRegion
ORDER BY CountryRegion
```

- To verify the above example, show the distinct pairs of country-state
```sql
USE adventureworks

SELECT DISTINCT 
    CountryRegion, 
    StateProvince
FROM SalesLT.Address
ORDER BY CountryRegion
```

**Ex 3: from `Product`, compute the average weight and list price by category**
```sql
USE adventureworks

SELECT 
    ProductCategoryID,
    AVG(Weight) AS avg_weight,
    AVG(ListPrice) AS avg_list_price
FROM SalesLT.Product
GROUP BY ProductCategoryID
ORDER BY ProductCategoryID
```

**Ex 4: from `SalesOrderDetail` table, compute the number of items, total revenue, average revenue per item for each order. Sort the result in descending order of total revenue**
```sql
-- Wrong solution
USE adventureworks

SELECT 
    SalesOrderID,
    COUNT(*) AS num_items,
    SUM(LineTotal) AS total_revenue,
    AVG(LineTotal) AS avg_revenue
FROM SalesLT.SalesOrderDetail
GROUP BY SalesOrderID
ORDER BY total_revenue DESC
```

```sql
--- Correct solution
USE adventureworks

SELECT 
    SalesOrderID,
    SUM(OrderQty) AS num_items,
    SUM(LineTotal) AS total_revenue,
    SUM(LineTotal) / SUM(OrderQty) AS avg_revenue
FROM SalesLT.SalesOrderDetail
GROUP BY SalesOrderID
ORDER BY total_revenue DESC
```

- Verify with order ID `71923`
```sql
SELECT *
FROM SalesLT.SalesOrderDetail
WHERE SalesOrderID = 71923
```

**Ex 5: redo Ex 4, but only for non-discount items**
```sql
USE adventureworks

SELECT 
    SalesOrderID,
    SUM(OrderQty) AS num_items,
    SUM(LineTotal) AS total_revenue,
    SUM(LineTotal) / SUM(OrderQty) AS avg_revenue
FROM SalesLT.SalesOrderDetail
WHERE UnitPriceDiscount = 0
GROUP BY SalesOrderID
ORDER BY total_revenue DESC
```
- Remarks: also verify with order ID `71923`

## GROUP BY with HAVING
**Ex 1: Redo Ex 5 above, but only keep the orders that have more than 100 items**
```sql
USE adventureworks

SELECT 
    SalesOrderID,
    SUM(OrderQty) as num_items,
    SUM(LineTotal) as total_revenue,
    SUM(LineTotal) / SUM(OrderQty) as avg_revenue
FROM SalesLsT.SalesOrderDetail
WHERE UnitPriceDiscount = 0
GROUP BY SalesOrderID
HAVING SUM(OrderQty) >= 100
ORDER BY total_revenue DESC
```

**Remarks**
- Do not confuse `HAVING` with `WHERE`
- We use `WHERE` to filter rows of the original data
- And use `HAVING` to filter rows of the results a `GROUP BY`
