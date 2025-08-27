# PostgreSQL Learning Roadmap: From Zero to Advanced

A practical, end‑to‑end plan to master SQL with PostgreSQL in 10–12 weeks (6–8 hrs/week). Postgres-first guidance, real datasets, and hands‑on milestones.

- Primary dialect: PostgreSQL (v15+ recommended)
- Target roles: Data/Analytics, Backend, or DBA
- Outcome: Confident querying, modeling, performance tuning, and real‑world operations in Postgres

---

## Table of Contents
- [1) Setup: Your PostgreSQL Stack (Day 1)](#1-setup-your-postgresql-stack-day-1)
- [2) Week-by-Week Roadmap (10–12 Weeks)](#2-week-by-week-roadmap-1012-weeks)
  - [Week 0: Setup and Foundations](#week-0-setup-and-foundations-)
  - [Week 1: Query Fundamentals](#week-1-query-fundamentals-)
  - [Week 2: Joins and Relationships](#week-2-joins-and-relationships-)
  - [Week 3: Aggregation and Grouping](#week-3-aggregation-and-grouping-)
  - [Week 4: Subqueries, CTEs, and Set Ops](#week-4-subqueries-ctes-and-set-ops-)
  - [Week 5: Window Functions (Analytics Powerhouse)](#week-5-window-functions-analytics-powerhouse-)
  - [Week 6: Data Modeling and DDL](#week-6-data-modeling-and-ddl-)
  - [Week 7: Transactions and Concurrency](#week-7-transactions-and-concurrency-)
  - [Week 8: Indexing and Performance](#week-8-indexing-and-performance-)
  - [Week 9: Database Objects, Extensions, and Programmability](#week-9-database-objects-extensions-and-programmability-)
  - [Week 10: Advanced PostgreSQL Features](#week-10-advanced-postgresql-features-)
  - [Week 11–12: Admin and Scaling Foundations](#week-1112-admin-and-scaling-foundations-)
- [3) Specialization Tracks](#3-specialization-tracks)
- [4) Practice Plan and Resources](#4-practice-plan-and-resources)
- [5) Capstone Ideas + Checklist](#5-capstone-ideas--checklist)
- [6) Common Pitfalls (Postgres‑Specific)](#6-common-pitfalls-postgres-specific-)
- [7) Suggested Timeline Summary](#7-suggested-timeline-summary)
- [8) Tailor This Plan for You](#8-tailor-this-plan-for-you)

---

## 1) Setup: Your PostgreSQL Stack (Day 1)

- Install PostgreSQL (v15+ or v16+).
  - macOS: `brew install postgresql@16`
  - Windows: EDB installer
  - Linux: apt/yum packages or Docker

- Tools:
  - GUI: DBeaver, TablePlus, pgAdmin
  - CLI: psql (bundled), pgcli (optional auto-complete)
  - Visualize plans: explain.dalibo.com, explain.depesz.com

- Sample databases:
  - dvdrental, Pagila (PostgreSQL port of Sakila), Northwind (PG variant)
  - Real data: Kaggle, IMDb, Stack Overflow, NYC taxi
  - Time-series: GitHub Archive, public COVID datasets

- Quick Docker start:
  ```bash
  docker run --name pg -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres:16
  # Connect with DBeaver/pgAdmin to localhost:5432 (user: postgres, db: postgres)
  ```

Tip: Load the dvdrental or Pagila sample and keep a scratch schema for experiments.

---

## 2) Week-by-Week Roadmap (10–12 Weeks)

### Week 0: Setup and Foundations 🌱
- Learn:
  - [ ] What a relational database is; schemas, tables, rows, columns
  - [ ] Keys: PRIMARY KEY, FOREIGN KEY; referential integrity
  - [ ] Core types: text, varchar, numeric, boolean, date, time, timestamp/timestamptz, interval
  - [ ] Powerful types: jsonb, arrays, enums, UUID, range (int4range, tsrange)
  - [ ] psql basics: `\l` (databases), `\c` (connect), `\dt` (tables), `\d table`, `\dn` (schemas), `\du` (roles)
  - [ ] Schemas and `search_path`
- Practice:
  - [ ] Create a database and schema; create/drop simple tables
  - [ ] Insert/select a few rows; explore `\d` output and constraints
- Milestone:
  - [ ] Comfortably connect, navigate, and run basic queries with psql/GUI

---

### Week 1: Query Fundamentals 🔍
- Learn:
  - [ ] SELECT, FROM, WHERE, ORDER BY, LIMIT/OFFSET, DISTINCT
  - [ ] Operators: =, <, >, BETWEEN, IN, LIKE/ILIKE, IS NULL
  - [ ] Functions: COALESCE, NULLIF, CAST and Postgres shorthand `::type`
  - [ ] Strings: CONCAT, SUBSTRING, POSITION, LOWER/UPPER, TRIM
  - [ ] Dates: NOW(), CURRENT_DATE, AGE(), DATE_TRUNC()
- Practice:
  - [ ] Answer 10 questions on a sample DB using filters/sorting
  - [ ] Use ILIKE for case-insensitive search; cast text->int safely
- Milestone:
  - [ ] Clean, readable queries with correct null and type handling

---

### Week 2: Joins and Relationships 🤝
- Learn:
  - [ ] INNER, LEFT/RIGHT/FULL OUTER, CROSS joins; self-joins
  - [ ] ON vs USING; when to avoid NATURAL joins
  - [ ] Many-to-many via junction tables; deduping and validation
- Practice:
  - [ ] Build 3–4 table reports, confirm counts match expectations
- Milestone:
  - [ ] Confidently select join types and validate row counts

---

### Week 3: Aggregation and Grouping 📊
- Learn:
  - [ ] GROUP BY, HAVING
  - [ ] Aggregates: COUNT, SUM, AVG, MIN, MAX
  - [ ] Postgres gems: STRING_AGG, ARRAY_AGG, FILTER clause for conditional aggregation
  - [ ] Advanced: GROUPING SETS, ROLLUP, CUBE
- Practice:
  - [ ] KPI reports (daily/weekly revenue, top-N)
- Milestone:
  - [ ] Accurate metrics with conditional and multi-level aggregations

---

### Week 4: Subqueries, CTEs, and Set Ops 🧩
- Learn:
  - [ ] Subqueries (scalar/correlated), EXISTS/NOT EXISTS
  - [ ] CTEs (WITH). PG12+ can inline CTEs; use MATERIALIZED/NOT MATERIALIZED deliberately
  - [ ] LATERAL joins (e.g., top-N per row/group)
  - [ ] UNION/UNION ALL, INTERSECT, EXCEPT
- Practice:
  - [ ] Compare cohorts/segments via CTE pipelines; LATERAL for top-K
- Milestone:
  - [ ] Decompose complex questions into readable, performant steps

---

### Week 5: Window Functions (Analytics Powerhouse) 🪟
- Learn:
  - [ ] OVER(), PARTITION BY, ORDER BY; frames (ROWS/RANGE)
  - [ ] ROW_NUMBER, RANK, DENSE_RANK, NTILE
  - [ ] LAG/LEAD, moving averages, running totals, percentiles
  - [ ] Postgres-specific: DISTINCT ON for “top-1 per group” when applicable
- Practice:
  - [ ] Cohort retention, top-K per group, trend metrics
- Milestone:
  - [ ] Replace many subqueries with concise window patterns

---

### Week 6: Data Modeling and DDL 🧱
- Learn:
  - [ ] Normalization (1NF/2NF/3NF, BCNF) and sensible denormalization
  - [ ] CREATE/ALTER TABLE; NOT NULL, DEFAULT, CHECK, UNIQUE, PRIMARY/FOREIGN KEY
  - [ ] DEFERRABLE constraints; ON DELETE/UPDATE actions (CASCADE/RESTRICT/SET NULL)
  - [ ] Identity/sequence options:
        - Prefer GENERATED {ALWAYS|BY DEFAULT} AS IDENTITY over legacy SERIAL
  - [ ] ENUMs vs lookup tables; DOMAINS for reusable constraints
- Practice:
  - [ ] Design and implement a normalized schema for a mini app
- Milestone:
  - [ ] Strong constraints and keys enforcing data integrity

---

### Week 7: Transactions and Concurrency 🔒
- Learn:
  - [ ] ACID; BEGIN/COMMIT/ROLLBACK; SAVEPOINT
  - [ ] MVCC and snapshots; isolation levels (Read Committed default, Repeatable Read, Serializable)
  - [ ] Locking: row locks (FOR UPDATE/NO KEY UPDATE), NOWAIT, SKIP LOCKED
  - [ ] Deadlocks, detection, and avoidance; advisory locks (pg_advisory_lock)
- Practice:
  - [ ] Reproduce a race condition; fix it with proper isolation/locking
- Milestone:
  - [ ] Confident, safe multi-session behavior under concurrency

---

### Week 8: Indexing and Performance ⚡
- Learn:
  - [ ] Index types: B-tree (default), GIN/GiST, SP-GiST, BRIN; Hash (niche)
  - [ ] Partial, multicolumn, expression, and covering indexes (INCLUDE)
  - [ ] JSONB indexing: GIN (jsonb_path_ops), trigram (pg_trgm) for LIKE/ILIKE
  - [ ] EXPLAIN/EXPLAIN ANALYZE; understanding seq scans vs index scans; JIT
  - [ ] Statistics and planner: ANALYZE, extended stats (CREATE STATISTICS)
  - [ ] Autovacuum, VACUUM/ANALYZE; bloat basics
- Practice:
  - [ ] 10x a slow query via index + rewrite; validate with plans
- Milestone:
  - [ ] Justify index choices with evidence and trade-offs

---

### Week 9: Database Objects, Extensions, and Programmability 🧠
- Learn:
  - [ ] Views vs Materialized Views; REFRESH MATERIALIZED VIEW CONCURRENTLY
  - [ ] Functions (PL/pgSQL), Procedures (CALL), Triggers; event triggers
  - [ ] COPY and \copy for fast CSV loads; Foreign Data Wrappers (postgres_fdw, file_fdw, http_fdw)
  - [ ] Popular extensions: uuid-ossp, pgcrypto, hstore, citext, pg_trgm, btree_gin, btree_gist, PostGIS
  - [ ] Scheduling: pg_cron extension or system cron + scripts
- Practice:
  - [ ] Materialized view pipeline with safe concurrent refresh
- Milestone:
  - [ ] Small, maintainable analytics or ETL pipeline in Postgres

---

### Week 10: Advanced PostgreSQL Features 🧭
- Time-series and analytics:
  - [ ] generate_series, date_trunc, gaps & islands
  - [ ] Range types + EXCLUDE constraints
- JSONB:
  - [ ] Operators: ->, ->>, @>, ?, ?|, ?&, jsonb_path_query
  - [ ] GIN indexes for JSONB; strategies for semi-structured data
- Full-text and fuzzy search:
  - [ ] tsvector/tsquery, to_tsvector/to_tsquery/plain phrase queries
  - [ ] GIN/GiST for FTS; pg_trgm for fuzzy matching/similarity
- Pivoting:
  - [ ] Conditional aggregation with FILTER; crosstab (tablefunc extension)
- Upserts and batching:
  - [ ] INSERT ... ON CONFLICT DO UPDATE; COPY for bulk ingest
- Milestone:
  - [ ] Analytics mart (star schema) + fast answers to 10 stakeholder questions

---

### Week 11–12: Admin and Scaling Foundations 🏗️
- Security:
  - [ ] Roles/privileges, least privilege, RLS (Row-Level Security) with policies
- Backup/restore:
  - [ ] pg_dump/pg_restore; logical vs physical backups
  - [ ] PITR with WAL archiving; pg_basebackup
- Replication and partitioning:
  - [ ] Streaming replication, logical replication (pub/sub)
  - [ ] Declarative partitioning (range/list/hash); pruning; global vs local indexes
- Monitoring and config:
  - [ ] pg_stat_statements, auto_explain; pg_stat_activity, pg_locks
  - [ ] Key settings: work_mem, shared_buffers, effective_cache_size, maintenance_work_mem
  - [ ] Connection pooling: PgBouncer
- Milestone:
  - [ ] Partition a large fact table; test backup/restore; add RLS for a multi-tenant table

---

## 3) Specialization Tracks

- Data Analyst / Analytics Engineer
  - Focus: window functions, CTE pipelines, JSONB querying, FTS basics
  - Tools: dbt with Postgres, BI (Metabase, Tableau, Power BI)
  - Extras: date dimension tables, SCD Type 2 in Postgres, data quality checks

- Backend Engineer
  - Focus: transactions, isolation, locking patterns, migrations (Sqitch/Flyway/Liquibase)
  - Extras: upserts, composite keys, JSONB vs normalized design, connection pooling, prepared statements

- Database Engineer / DBA
  - Focus: indexing strategy, planner/stats, autovacuum tuning, replication/failover
  - Extras: partitioning, PITR drills, security hardening, monitoring stack (Prometheus + Grafana, pganalyze/pgwatch2)

---

## 4) Practice Plan and Resources

- Routine (5x/week)
  - 60–90 minutes:
    - Learn (20–30m) → Exercises (30–40m) → Open-ended (10–20m) → Notes

- Interactive practice (Postgres-focused)
  - pgExercises, DB Fiddle (Postgres), HackerRank SQL, LeetCode Database
  - Official docs (gold standard): postgresql.org/docs

- Datasets
  - dvdrental, Pagila; Kaggle retail/rideshare; TPC-H; Stack Overflow

- Validation milestones
  - [ ] Queries covering all join types + correct counts
  - [ ] Window-based top-K, running totals, percentiles
  - [ ] EXPLAIN ANALYZE to justify indexes; partial/expression indexes where useful
  - [ ] Solid DDL with identity columns, constraints, and FKs
  - [ ] COPY-based ETL and a scheduled refresh job (pg_cron)

---

## 5) Capstone Ideas + Checklist

- Project ideas
  - E-commerce analytics: orders, customers, products; JSONB for event payloads; FTS for product search
  - Ride-hailing/food delivery: trips, drivers, surge; range types for availability; time-series dashboards
  - Event tracking: sessions/events; rolling retention; pg_trgm for fuzzy user lookup
  - Finance: trades/orders/positions; as-of joins; partitioned fact tables

- Checklist
  - [ ] Model: ERD + DDL (identity columns, constraints, indexes)
  - [ ] Load: COPY/\copy from CSV → staging → marts; validation queries
  - [ ] Queries: 20+ from basics to advanced windows and JSONB
  - [ ] Performance: partial/expression indexes; materialized views; EXPLAIN before/after
  - [ ] Ops: backup/restore test; RLS for multi-tenant schema; simple replication

---

## 6) Common Pitfalls (Postgres‑Specific)

- Overusing CTEs as “optimization fences” (PG12+ can inline; use MATERIALIZED if you need a fence)
- Using SERIAL instead of modern GENERATED AS IDENTITY
- Confusing timestamp vs timestamptz (always prefer timestamptz unless you truly need “naive” time)
- Ignoring ANALYZE: stale stats lead to bad plans; schedule ANALYZE after big loads
- Too many low-selectivity indexes; forgetting partial or expression indexes
- Missing COLLATION/ICU considerations for case/locale-sensitive sorts/searches
- Using DISTINCT to mask join errors; fix joins or use DISTINCT ON purposefully
- Large DELETEs without batching/VACUUM; consider partitioning or soft-deletes when appropriate

---

## 7) Suggested Timeline Summary

- Weeks 0–5: Querying mastery (joins, aggregates, CTEs, windows)
- Weeks 6–8: Modeling, constraints, transactions, indexing
- Weeks 9–10: Extensions, views, stored code, JSONB, FTS
- Weeks 11–12: Admin/scaling fundamentals, partitioning, replication, capstone polish

---

## 8) Tailor This Plan for You

Share:
- Your target role (data vs backend vs DBA)
- Time commitment per week and your target date
- OS and whether you prefer Docker

I’ll generate a focused 2–3 week checklist with exercises, a ready-to-load dvdrental/Pagila schema, and a set of practice questions matched to your goals.

---

### Quick PostgreSQL Cheatsheet

- Identity column:
  ```sql
  CREATE TABLE users (
    user_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    email CITEXT UNIQUE NOT NULL
  );
  ```
- Upsert:
  ```sql
  INSERT INTO users(email) VALUES ('a@b.com')
  ON CONFLICT (email) DO UPDATE SET email = EXCLUDED.email;
  ```
- JSONB index for search:
  ```sql
  CREATE INDEX users_profile_gin ON users USING GIN (profile jsonb_path_ops);
  ```
- Trigram index for ILIKE:
  ```sql
  CREATE EXTENSION IF NOT EXISTS pg_trgm;
  CREATE INDEX users_email_trgm ON users USING GIN (email gin_trgm_ops);
  -- speeds up WHERE email ILIKE '%abc%'
  ```
- View + materialized view:
  ```sql
  CREATE VIEW v_daily AS
  SELECT date_trunc('day', created_at)::date AS d, count(*) AS c FROM events GROUP BY 1;

  CREATE MATERIALIZED VIEW mv_daily AS
  SELECT date_trunc('day', created_at)::date AS d, count(*) AS c FROM events GROUP BY 1;
  -- Later:
  REFRESH MATERIALIZED VIEW CONCURRENTLY mv_daily;
  ```

Happy querying with PostgreSQL! 🚀
