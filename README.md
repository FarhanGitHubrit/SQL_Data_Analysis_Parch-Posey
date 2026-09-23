SQL for Data Analysis — Parch & Posey

SQL Tool License Show Image

A structured, progressively advancing collection of SQL exercises and solutions written against the Parch & Posey sample database, using PostgreSQL. This repo moves from basic SELECT/WHERE statements through joins, aggregations, subqueries/CTEs, window functions, and advanced join techniques — each file is self-contained, commented with the original problem statement, and ordered by difficulty.

Originally based on the Udacity "SQL for Data Analysis" course (in partnership with Mode Analytics); solutions, notes, and additional exploratory queries are my own.

Table of Contents
Database Overview
Entity Relationship Diagram
Repository Structure
Topics Covered
Getting Started
How to Use This Repo
Sample Query
Tech Stack
Roadmap
Acknowledgements
License
Database Overview

The Parch & Posey database simulates a B2B paper sales company. It contains five related tables:

Table	Description
accounts	Customer companies — name, website, geo-coordinates, primary point of contact, and assigned sales rep
orders	Paper orders placed by accounts — quantities and USD amounts across standard, gloss, and poster paper types
web_events	Marketing touch-points per account — channel and timestamp
sales_reps	Sales representatives, each tied to a region
region	Sales regions
Entity Relationship Diagram

Show Image

accounts.sales_rep_id → sales_reps.id
sales_reps.region_id → region.id
orders.account_id → accounts.id
web_events.account_id → accounts.id
Repository Structure
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
Topics Covered
#	File	Key Concepts
1	Basic SQL	SELECT, WHERE, ORDER BY, LIMIT, LIKE, IN / NOT IN, BETWEEN, compound AND/OR logic
2	SQL Joins	INNER JOIN across multiple tables, aliasing, filtering joined data
3	Aggregations	SUM, AVG, MIN, MAX, COUNT, GROUP BY, HAVING, CASE WHEN, DATE_PART, median via ordering
4	Subqueries & Temp Tables	Nested subqueries, derived tables, WITH (CTEs), multi-CTE chaining
5	Data Cleaning	LEFT/RIGHT, POSITION/STRPOS, CONCAT/||, COALESCE, string parsing for emails/passwords
6	Window Functions	OVER (PARTITION BY ... ORDER BY ...), RANK, DENSE_RANK, NTILE, LEAD/LAG, named window (WINDOW) clauses
7	Advanced Joins	FULL OUTER JOIN, inequality joins, self joins, UNION vs UNION ALL, EXPLAIN for performance tuning
Getting Started
Prerequisites
PostgreSQL installed locally (or access to a Postgres instance)
pgAdmin4 or any SQL client of your choice
The Parch & Posey schema + CSV seed data (see Acknowledgements for the source)
