---
title: The select statement
date: 2022-10-20
---

## Full syntax for a `SELECT` statement
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
WHERE <cond> -- filtering condition for rows
GROUP BY <cols> -- list of columns to group on
HAVING <cond> -- filtering condition for grouped data
ORDER BY <cols> -- list of columns to order by
```

## SELECT FROM
**Syntax**
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
```

### Select everything
**Ex1 : select every row and column from `Customer` (LT)**
- Be aware if the table has many rows
```sql
USE adventureworks

SELECT *
FROM SalesLT.Customer
```

### Select first N rows
**Ex 1: select first 10 rows and all columns from `Customer` (LT)**
- Good practice for previewing the data
- From now on, `select top N rows` is the default action when we just want to preview the output
```sql
USE adventureworks

SELECT TOP 10 *
FROM SalesLT.Customer
```

### Select just some columns
**Ex 1: select some columns from `Customer` (LT)**
- Pull out `Title`, `FirstName`, `MiddleName`, `LastName`, `CompanyName`, and `Phone` from `Customer` (LT)
```sql
USE adventureworks

SELECT TOP 10
    Title,
    FirstName,
    MiddleName,
    LastName,
    CompanyName,
    Phone
FROM SalesLT.Customer
```

### Select columns using alias
**Ex 1: Select `Title`, `FirstName`, `LastName`, `Phone` and rename them to `danh_xung`, `ten`, `ho`, `dien_thoai`**
```sql
USE adventureworks

SELECT TOP 10
    Title AS danh_xung,
    FirstName AS ten,
    LastName AS ho,
    Phone AS dien_thoai
FROM SalesLT.Customer
```

**Ex 2: `AS` is optional**
```sql
USE adventureworks

SELECT TOP 10
    Title danh_xung,
    FirstName ten,
    LastName ho,
    Phone dien_thoai
FROM SalesLT.Customer
```

**Ex 3: when new names have spaces**
- For column names with spaces (Ex: in Vietnamese), we wrap them in single or double quotes (`'` or `"`)
- Ex: select `Title`, `FirstName`, `LastName`, `Phone` and rename them to `Danh xưng`, `Tên`, `Họ`, `Điện thoại`
```sql
USE adventureworks

SELECT TOP 10
    Title AS "Danh xưng",
    FirstName AS "Tên",
    LastName AS "Họ",
    Phone AS "Điện thoại"
FROM SalesLT.Customer
```

### Select new columns from the originals
**Ex 1: select new columns using string concatenation**
- Select full name from `Title`, `FirstName`, `LastName` 
- Also select `Phone` and `EmailAddress`
```sql
USE adventureworks

SELECT TOP 10
    Title + ' ' + FirstName + ' ' + LastName AS FullName,
    Phone,
    EmailAddress
FROM SalesLT.Customer
```

**Ex 2: select new columns using math operators**
- Create `Revenue` column from the original data
- Also select `SalesOrderID`, `OrderQty`, `UnitPrice`, `UnitPriceDiscount`, `LineTotal` 
- Verify the result by comparing `Revenue` and `LineTotal`
```sql
USE adventureworks

SELECT TOP 10
    SalesOrderID,
    OrderQty, 
    UnitPrice, 
    UnitPriceDiscount,
    LineTotal,
    OrderQty * UnitPrice * (1 - UnitPriceDiscount) AS Revenue
FROM SalesLT.SalesOrderDetail
```

### Count number of rows
**Ex: count number of rows in `Product` (LT)**
- Will learn in detail later when introducing aggregation operations
```sql
USE adventureworks

SELECT count(*)
FROM SalesLT.Product
```

## SELECT WHERE
**Syntax**
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
WHERE <cond> -- filtering condition for rows
```
### Ways to create conditions
- Using comparisons such as `=, !=, >, <`
- Using `IN`
- Using `IS/IS NOT` for missing data
- Using `LIKE` for string data

### Conditions using comparisons
Comparison operators
- Equal: `=`
- Not equal: `<>` or `!=`
- Greater than: `>`
- Greater than or equal: `>=`
- Less than `<`
- Less than or equal: `<=`

**Preview `Product` (LT)**
```sql
USE adventureworks

SELECT TOP 10 *
FROM SalesLT.Product
```

**Ex 1: extract products with `ListPrice` no more than `1,000`**
```sql
USE adventureworks

SELECT TOP 10 *
FROM SalesLT.Product
WHERE ListPrice <= 1000
```

**Ex2: extract products with white color**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Color = 'White'
```

**Ex 3: extract products with colors other than white**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Color != 'White'
```

### Conditions using `IN`
**Ex 1: extract products with black, white, or red colors**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Color IN ('Black', 'White', 'Red')
```

**Ex 2: extract product with model ID `6`, `11`, `18`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE ProductModelID IN (6, 11, 18)
```

### Conditions using `IS` with missing data
- In SQL, missing data is represented by `NULL`
- To select/de-select `NULL` values, we use `IS NULL` or `IS NOT NULL`
- Note: do not confuse `NULL` with `'NULL'`
    - `NULL` is an SQL keyword indicating missing values
    - `'NULL'` is a string of 4 characters

**Preview `Product` (LT)**
```sql
USE adventureworks

SELECT TOP 20 *
FROM SalesLT.Product
```

**Ex 1: extract products that DO NOT have information about `Weight`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Weight IS NULL
```

**Ex 2: extract products that DO have information about `Weight`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Weight IS NOT NULL
```

**Remarks**
- When using regular conditions such as comparison or `IN`, conditions involving `NULL` will always return `FALSE`, thus the corresponding rows will NOT be selected
- Example: `WHERE Weight >= 20`, only rows that have `Weight` data **AND** `Weight >= 20` are selected

### Conditions using `LIKE` with string data
- **Wildcard characters**
    - `%`: zero or more characters
    - `_`: single characters
    - `[]`: any single characters listed in the brackets
    - `^[]`: any characters not in the brackets
- Examples
    - `'X'`: exactly `X` (just like using equality `=`)
    - `'%X%'`: contain `'X'`
    - `X%`: start with `X` and followed by anything
    - `%X`: end with `X` and start with anything
    - `X_%`: start with `X` and followed by at least 1 character (i.e., at least of 2 characters in length)
    - `%__X`: end with `x` and at least 3 characters in length
    - `X%Z`: start with `X` and end with `Z`
- Notes on **case-sensitivity**
    - By default, an SQL Server DB is case-insensitive, and thus `ABC`, `Abc`, and `abc` are the same in string comparisons
    - Other DBMS might have different default configuration (for example, PostgreSQL is case-sensitive by default)

#### Exact match
**Ex 1: extract products with exact name `AWC Logo Cap`** using `LIKE`
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name LIKE 'AWC Logo Cap'
```

**Ex 2: extract products with exact name `AWC Logo Cap`** using `=`
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name = 'AWC Logo Cap'
```

#### Contain
**Ex 1: extract products whose names contains `Ca`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name LIKE '%Ca%'
```

**Ex 2: extract products whose names contains `Ca`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name LIKE '%Ca%'
-- You can try with '%CA%' or '%ca%'
```

**Ex 3: extract products whose names contains `Re` using case-sensitive matching**
```sql
-- Case-sensitive
-- Insert COLLATE Latin1_General_CS_AS before LIKE
USE AdventureWorksLT2019

SELECT Name
FROM SalesLT.Product
WHERE Name COLLATE Latin1_General_CS_AS LIKE '%Re%'
```

**Ex 4: extract products whose name contain `re` regardless upper/lower cases for all DBMS**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE LOWER(Name) LIKE '%re%'
```

#### Start with
**Ex 1: extract products whose names start with `Short`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name LIKE 'Short%'
```

#### End with
**Ex 1: extract products whose names ends with `, M`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Name LIKE '%, M'
```

### Multiple conditions with logical operators
- Logical operators include `AND`, `OR`, `NOT`
- We can use logical operators to combine multiple conditions together

#### Logical AND
**Ex 1: extract products that have `tire` (case-insensitive) in name and list price less than `30`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (LOWER(Name) LIKE '%tire%')
    AND (ListPrice < 30)
```

**Ex 2: extract yellow sleeve with list price more than 50**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (LOWER(Name) LIKE '%sleeve%')
    AND (Color = 'Black')
    AND (ListPrice > 50)
```

**Ex 3: extract any products with black color and having standard cost between `20` and `40` (inclusive)**

```sql
-- Method 1: using comparison operators
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (Color = 'Black')
    AND (StandardCost >= 20)
    AND (StandardCost <= 40)
```

```sql
-- Method 2: using BETWEEN
-- Note that two end values are INCLUDED
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (Color = 'Black')
    AND (StandardCost BETWEEN 20 AND 40)
```

#### Logical OR
**Ex 1: select products that have red or white colors**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE
    (Color = 'Red')
    OR (Color = 'White')
```
Note: using `IN` is better for this example

**Ex 2: select product that have list price `< 10` or `> 3000`**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE
    (ListPrice < 10)
    OR (ListPrice > 3000)
```

#### Logical NOT
**Ex 1: select all products except ones with red color**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Color NOT LIKE 'Red'
```
Remarks
- As mentioned earlier, this regular comparison will not return rows with `NULL` color
- To select all rows whose colors are not red, including rows with `NULL` color, we have to add another clause using `OR` as in Ex 2 below

**Ex 2: select all products except ones with red color, including rows with NULL color**

```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (Color NOT LIKE 'Red')
    OR (Color IS NULL)
```

## SELECT ORDER BY
- We use `ORDER BY` when we want to sort data
- We can sort data by one or multiple columns
- **Syntax**
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
ORDER BY <cols> -- list of columns to order by
```

### Sort by single column
**Ex 1: sort product by `Color` (ascending or ASC)**
- Note that in SQL Server, when sorting in an ascending order, `NULL` values appear first
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
ORDER BY Color ASC
```

**Ex 2: `ASC` is optional**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
ORDER BY Color
```

**Ex 3: sort products by `Color` (descending or DESC)**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
ORDER BY Color DESC
```


**Ex 4: sort products by `Color` (ASC) but ignore NULL rows**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE Color IS NOT NULL
ORDER BY Color 
```

### Sort by multiple columns
**Ex 1: sort products by `Color` (ASC), then by `Weight` (DESC) and ignore `NULL` rows**
```sql
USE adventureworks

SELECT *
FROM SalesLT.Product
WHERE 
    (Color IS NOT NULL)
    AND (Weight IS NOT NULL)
ORDER BY Color, Weight DESC
```

## SELECT DISTINCT
- `SELECT DISTINCT` allows us to remove duplicates and get only unique values
- **Syntax**
```sql
SELECT DISTINCT <cols> -- list of columns to return
FROM <tbl>
```

### Distinct values of one column
**Ex 1: extract unique product sizes**
```sql
USE adventureworks

SELECT DISTINCT Size
FROM SalesLT.Product
ORDER BY Size -- Optional
```
Note: try with other columns such as `Color`, `ProductModelID`, `ProductCategoryID`

### Distinct values of multiple columns
**Ex 1: extract unique pair of colors and sizes**
```sql
USE adventureworks

SELECT DISTINCT Color, Size
FROM SalesLT.Product
ORDER BY Color, Size -- Optional
```

### Count number of distinct values
**Ex 1: count number of unique colors**
- Note that `NULL` is NOT counted
```sql
USE adventureworks

SELECT COUNT(DISTINCT Color)
FROM SalesLT.Product
```

## Summary
**Full syntax for a `SELECT` statement**
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
WHERE <cond> -- filtering condition for rows
GROUP BY <cols> -- list of columns to group on
HAVING <cond> -- filtering condition for grouped data
ORDER BY <cols> -- list of columns to order by
```

**SELECT FROM**
- Syntax
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
```
- Select all columns: `SELECT *`
- Select top N rows: `SELECT TOP N`
- Select some columns: `SELECT col_1, col_2, ...`
- Select using column aliases: `SELECT col_1 AS alias_1, ...`
- Select new columns from originals: `SELECT expr AS new_col`
- Count number of rows: `SELECT COUNT(*)`

**SELECT WHERE**
- Syntax
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
WHERE <cond> -- filtering condition for rows
```
- Ways to create conditions
    - Using comparisons such as `=, !=, >, <`
    - Using `IN`
    - Using `IS/IS NOT` for missing data
    - Using `LIKE` for string data
- Combine multiple conditions using logical operators `AND`, `OR`, and `NOT`

**SELECT ORDER BY**
- Syntax
```sql
SELECT <cols> -- list of columns to return
FROM <tbl> -- location of the table
ORDER BY <cols> -- list of columns to order by
```

**SELECT DISTINCT**
- Syntax for select distinct
```sql
SELECT DISTINCT <cols> -- list of columns to return
FROM <tbl>
```
- Syntax for count distinct
```sql
SELECT COUNT(DISTINCT col)
FROM <tbl>
```