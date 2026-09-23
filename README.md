# SQL for Data Analysis — Parch & Posey

A structured, progressively advancing collection of SQL exercises and solutions written against the **Parch & Posey** sample database, using **PostgreSQL**. This repo moves from basic `SELECT`/`WHERE` statements through joins, aggregations, subqueries/CTEs, window functions, and advanced join techniques — each file is self-contained, commented with the original problem statement, and ordered by difficulty.

Originally based on the Udacity **"SQL for Data Analysis"** course (in partnership with Mode Analytics); solutions, notes, and additional exploratory queries are my own.

---

## Table of Contents

- [Database Overview](#database-overview)
- [Entity Relationship Diagram](#entity-relationship-diagram)
- [Repository Structure](#repository-structure)
- [Topics Covered](#topics-covered)
- [Getting Started](#getting-started)
- [How to Use This Repo](#how-to-use-this-repo)
- [Sample Query](#sample-query)
- [Tech Stack](#tech-stack)
- [Roadmap](#roadmap)
- [Acknowledgements](#acknowledgements)
- [License](#license)

---

## Database Overview

The **Parch & Posey** database simulates a B2B paper sales company. It contains five related tables:

| Table         | Description                                              |
|---------------|-----------------------------------------------------------|
| `accounts`    | Customer companies — name, website, geo-coordinates, primary point of contact, and assigned sales rep |
| `orders`      | Paper orders placed by accounts — quantities and USD amounts across `standard`, `gloss`, and `poster` paper types |
| `web_events`  | Marketing touch-points per account — channel and timestamp |
| `sales_reps`  | Sales representatives, each tied to a region |
| `region`      | Sales regions |

## Entity Relationship Diagram

![Parch & Posey ERD](The_Parch___Posey_Database_ERD.png)

- `accounts.sales_rep_id → sales_reps.id`
- `sales_reps.region_id → region.id`
- `orders.account_id → accounts.id`
- `web_events.account_id → accounts.id`

## Repository Structure
├── 01_Basic_SQL.sql # SELECT, WHERE, ORDER BY, LIMIT, LIKE, IN, BETWEEN
├── 02_SQL_Join.sql # INNER JOIN across accounts / orders / sales_reps / region
├── 03_SQL_Aggregrations.sql # SUM, AVG, MIN/MAX, COUNT, GROUP BY, HAVING, CASE, DATE_PART
├── 04_Sub_Queries___Temporary_Tables.sql # Subqueries, derived tables, CTEs (WITH)
├── 05_SQL_Data_Cleaning.sql # LEFT/RIGHT, POSITION/STRPOS, CONCAT, COALESCE
├── 06__Advanced_SQL_Window_Functions.sql # OVER/PARTITION BY, RANK, NTILE, LEAD/LAG, window aliases
├── 07__Advanced_SQL_Advanced_JOINS.sql # FULL OUTER JOIN, self joins, inequality joins, UNION, EXPLAIN
├── The_Parch___Posey_Database_ERD.png # Schema diagram
└── README.md
