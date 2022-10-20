---
title: Sample data
date: 2022-10-20
---

## Sample data
- We will use `AdventureWorks` DB for practice
- This DB contains simulated data for a fictional retail company
- We will use 2 versions of this DB throughout the course
    - `adventureworks`
        - The lightweight (LT) version (simpler)
        - Only 2 schemas: `dbo`, `SalesLT`
        - ERD: https://sqlzoo.net/wiki/AdventureWorks
    - `adventureworksFull`
        - The full version (more complex)
        - Many schemas: `dbo`, `Person`, `Production`, `Sales`, `Purchasing`, ...
        - ERD: https://dataedo.com/samples/html/AdventureWorks/doc/AdventureWorks_2/home.html

## Locating data
- To access the data, you must know where they reside
- We locate data using both absolute and relative paths
- **Absolute paths**
    - You are at the **entrance of your server**
    - **Syntax:** `db_name.schema_name.object_name`
- **Relative paths**
    - You are already at the **entrance a specific DB**
    - **Syntax:** `schema_name.object_name`
    - **Note:** if the schema is `dbo`, the syntax is reduced to just `object_name` (note that we can only do this while using relative paths)

**Ex 1: view first 5 rows in table `BuildVersion` of LT version**

```sql
-- Use an absolute path
-- Path: db_name.schema_name.tbl_name
SELECT TOP(5) *
FROM adventureworks.dbo.BuildVersion
```

```sql
-- Use a relative path
-- schema_name.tbl_name
USE adventureworks

SELECT TOP(5) *
FROM dbo.BuildVersion
```

```sql
-- Use a relative path, but drop dbo
-- Path: tbl_name
USE adventureworks

SELECT TOP(5) *
FROM BuildVersion
```

**Remarks**
- `--` indicates a **comment**
    - Comments are ignore during execution
    - They are used only to document/explain our code
- From now on, if not specified, we will **use relative paths** when writing queries because it is more convenient

**Ex 2: view first 5 rows in table `Address` of LT version**
```sql
-- You must specify the schema 
-- because SalesLT is not the default schema
-- Path: schema_name.tbl_name
USE adventureworks

SELECT TOP(5) *
FROM SalesLT.Address
```

**Ex 3: view first 5 rows in table `Customer` of Full version**

```sql
-- Absolute path
SELECT TOP(5) *
FROM AdventureWorks2019.Person.Person
```

```sql
-- Relative path
USE AdventureWorks2019

SELECT TOP(5) *
FROM Person.Person
```

## Types of SQL statements
- **Data Manipulation Language (DML)**
    - Statements for querying and modifying data
    - SELECT, INSERT, UPDATE, DELETE
- **Data Definition Language (DDL)**
    - Statements for defining DB objects (such as tables)
    - CREATE, ALTER, DROP
- **Data Control Language (DCL)**
    - Statements for assigning security permissions
    - GRANT, REVOKE, DENY
- As a DA, we mostly use DML (DDL and DCL are skills required for DBA and DE)


