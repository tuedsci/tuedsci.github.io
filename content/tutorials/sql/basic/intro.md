---  
title: Introduction to SQL
---

## What is SQL?

### Informal definition

SQL stands for Structured Query Language. It is the language we, as humans, use to communicate with databases. Think of a database as a foreigner (an arrogant one). This foreigner doesn't know our language, and since he is arrogant, he will never try to learn ours. To communicate and work with him, we must learn the language that he understands, i.e., SQL.

### Formal definition

SQL is a domain-specific language designed for managing and manipulating data stored in relational database management systems (or DBMSs).

### How to pronounce

There are two common ways to pronounce the term SQL: `/es kju: el/`
and `/si:kwəl/`.

## Why learn SQL?

Most people learn SQL not because it's fun or because it can help them in their personal lives. If you want to manage and process data at the personal level, SQL is probably overkilled. Instead, a simple spreadsheet application such as Microsoft Excel, Libre Calculator, or Google Sheets might be a better
alternative.

People learn SQL because companies nowadays store their data in relational DBMSs, and they want those who can work with the massive data and extract insights that help the organizations make actionable (and hopefully profitable) decisions. In short, companies want those who can "speak" SQL.

Thus, if you cannot think of any good reasons, then "enhancing career prospects" might be an appropriate motivation to start learning SQL.

## SQL vs. DBMS

People are often confused between these two concepts. They are related but are different animals.

> SQL is a language, while DBMS is a kind of software.

We use a DBMS (software) to store and process data, but we need to provide our instructions using SQL (language). Otherwise, the DBMS could not understand.

## SQL variants

Here is an interesting fact: there is more than one kind of SQL. You might have heard of PostgreSQL, SQL Server, MariaDB, and so on. They are not SQL; they are DBMSs. However, these DBMSs do not speak the same language. Each of them adopts a slightly different variation of the standard SQL. For example

- PostgreSQL (software) uses PL/pgSQL (language)
- SQL Server (software) uses T-SQL (language)

But often, there is no official name for the SQL variant that a DBMS uses.

However, the good news is that all SQL variants are almost the same because they all follow the standard guideline proposed by the American National Standards Institute (ANSI). Thus, if you learn PostgreSQL (that speaks PL/pgSQL) and later get a job in a company that uses SQL Server (that speaks
T-SQL), then you will be perfectly fine.

I think the following analogy would help. Think of an English-speaking country like a DBMS, and the kind of English its people speak is an SQL dialect (as in the table below)

| DBMS   | SQL variant      |
| ------ | ---------------- |
| US     | American English |
| UK     | British English  |
| Canada | Canadian English |

For most of the time, American and British can perfectly understand each other regardless of the kinds of English they use. But there are times when a word in American might mean a different thing in British (e.g., football).

Take a look at the following example: let's say we want to get the first 5 rows in the `Customer` table.

Here is how we talk to PostgreSQL.

```sql
SELECT *
FROM Customer
LIMIT 5
```

And here is how we talk to SQL Server.

```sql
SELECT TOP 5 *
FROM Customer
```
