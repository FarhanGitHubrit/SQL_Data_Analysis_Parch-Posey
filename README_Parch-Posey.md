# SQL for Data Analysis — Parch & Posey

[![SQL](https://img.shields.io/badge/SQL-PostgreSQL-336791?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Tool](https://img.shields.io/badge/Client-pgAdmin4-blue)](https://www.pgadmin.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](#license)
[![Status](https://img.shields.io/badge/status-complete-brightgreen)]()

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

```
sql-for-data-analysis/
├── 01_Basic_SQL.sql                        # SELECT, WHERE, ORDER BY, LIMIT, LIKE, IN, BETWEEN
├── 02_SQL_Join.sql                         # INNER JOIN across accounts / orders / sales_reps / region
├── 03_SQL_Aggregrations.sql                # SUM, AVG, MIN/MAX, COUNT, GROUP BY, HAVING, CASE, DATE_PART
├── 04_Sub_Queries___Temporary_Tables.sql   # Subqueries, derived tables, CTEs (WITH)
├── 05_SQL_Data_Cleaning.sql                # LEFT/RIGHT, POSITION/STRPOS, CONCAT, COALESCE
├── 06__Advanced_SQL_Window_Functions.sql   # OVER/PARTITION BY, RANK, NTILE, LEAD/LAG, window aliases
├── 07__Advanced_SQL_Advanced_JOINS.sql     # FULL OUTER JOIN, self joins, inequality joins, UNION, EXPLAIN
├── The_Parch___Posey_Database_ERD.png      # Schema diagram
└── README.md
```

## Topics Covered

| # | File | Key Concepts |
|---|------|---------------|
| 1 | Basic SQL | `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`, `LIKE`, `IN` / `NOT IN`, `BETWEEN`, compound `AND`/`OR` logic |
| 2 | SQL Joins | `INNER JOIN` across multiple tables, aliasing, filtering joined data |
| 3 | Aggregations | `SUM`, `AVG`, `MIN`, `MAX`, `COUNT`, `GROUP BY`, `HAVING`, `CASE WHEN`, `DATE_PART`, median via ordering |
| 4 | Subqueries & Temp Tables | Nested subqueries, derived tables, `WITH` (CTEs), multi-CTE chaining |
| 5 | Data Cleaning | `LEFT`/`RIGHT`, `POSITION`/`STRPOS`, `CONCAT`/`\|\|`, `COALESCE`, string parsing for emails/passwords |
| 6 | Window Functions | `OVER (PARTITION BY ... ORDER BY ...)`, `RANK`, `DENSE_RANK`, `NTILE`, `LEAD`/`LAG`, named window (`WINDOW`) clauses |
| 7 | Advanced Joins | `FULL OUTER JOIN`, inequality joins, self joins, `UNION` vs `UNION ALL`, `EXPLAIN` for performance tuning |

## Getting Started

### Prerequisites
- PostgreSQL installed locally (or access to a Postgres instance)
- [pgAdmin4](https://www.pgadmin.org/) or any SQL client of your choice
- The Parch & Posey schema + CSV seed data (see [Acknowledgements](#acknowledgements) for the source)

### Setup

```bash
# Clone the repository
git clone https://github.com/<your-username>/sql-for-data-analysis.git
cd sql-for-data-analysis

# Restore the schema/data dump into a fresh database
createdb parch_and_posey
psql -d parch_and_posey -f schema_dump.sql
```

Then open any `.sql` file in pgAdmin4 (or `psql`) and run queries individually — each is commented with its original prompt directly above the solution.

## How to Use This Repo

Each `.sql` file follows the same convention:

```sql
/* Problem statement / question goes here */
SELECT ...
FROM ...
WHERE ...;
```

This makes the files usable as:
- **A reference** — jump to a topic (e.g. window functions) and see idiomatic PostgreSQL patterns
- **A practice set** — hide the query, read the comment, try to write your own solution first
- **Interview prep** — the progression basic → joins → aggregation → subqueries → window functions mirrors how SQL is typically tested

## Sample Query

Ranking each account's orders by total paper purchased, using a window function (from file 06):

```sql
SELECT id, account_id, total,
    RANK() OVER (PARTITION BY account_id ORDER BY total DESC) AS total_rank
FROM orders;
```

## Tech Stack

- **Database:** PostgreSQL
- **Client:** pgAdmin4
- **Data:** Parch & Posey sample CSV dataset

## Roadmap

- [ ] Add the schema dump / CSV seed files directly to the repo
- [ ] Add `EXPLAIN ANALYZE` comparisons for the performance-tuning queries in file 07
- [ ] Port select queries to an equivalent dbt / pandas notebook for cross-tool comparison

## Acknowledgements

- Exercises adapted from Udacity's **[SQL for Data Analysis](https://in.udacity.com/course/sql-for-data-analysis--ud198)** course, created in partnership with [Mode Analytics](https://modeanalytics.com/).
- Parch & Posey is a fictional dataset used purely for educational purposes.

## License

This project is licensed under the [MIT License](LICENSE) — feel free to fork, use, and adapt for your own learning.
