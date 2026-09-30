---
name: data
description: Databases, SQL, migrations, queries, indexes, and data integrity. Triggers on "sql", "query", "database", "migration", "index", "slow query", "schema", "postgres", "sqlite", "duplicate rows", "n+1", "schema change".
---

# Data

## When to use

State that has to survive a restart, or a query that has to survive production volume.

## Rules

- Schema decisions are forever. Everything else is cheap to change. Take the extra minute here.
- Every migration needs a down path, and the down path gets tested, not assumed.
- Migrations are additive first: add the column, backfill, switch reads, then drop. One deploy doing all
  four means one deploy that can break.
- Constraints in the database beat validation in the application. A unique index is a rule the code
  cannot forget.
- Default to a foreign key and real transactions over application-level coordination. Two writes that
  must agree belong in one transaction.
- Every query gets an `EXPLAIN` before it gets a cache. A missing index is a design bug, not a perf bug.
- Watch for the N+1: count queries in a loop, then decide whether to eager-load or batch.
- Parameterize every query. No string-built SQL, ever, not even for a constant.
- Destructive statements (`DROP`, `TRUNCATE`, `DELETE` without `WHERE`) need explicit consent and a count
  of rows about to go.
- Data truth lives in one place. Two tables that must agree get a constraint or a transaction, not a
  nightly job that fixes the difference.
- Do not store what can be derived. A cached column is a bug waiting for the day the derivation changes.

## Done when

- The migration runs forward and backward, on a copy of production-shaped data.
- Query plans were checked for anything touching a growing table.
