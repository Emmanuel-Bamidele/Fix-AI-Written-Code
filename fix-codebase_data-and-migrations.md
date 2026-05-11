# fix-codebase_data-and-migrations.md

Use this prompt to review database schema, migrations, data safety, and persistence logic.

## Goal

Prevent data loss, corruption, unsafe migrations, and incorrect persistence behavior.

## Agent instructions

Treat database changes as high risk.

Review:

- Schema
- Migrations
- Seed data
- ORM models
- Query code
- Transactions
- Backfills
- Soft deletes
- Cascading deletes
- Indexes
- Constraints

## Schema checklist

- [ ] Primary keys exist.
- [ ] Foreign keys exist where appropriate.
- [ ] Unique constraints match business rules.
- [ ] Not-null constraints are safe.
- [ ] Defaults are deliberate.
- [ ] Indexes support real queries.
- [ ] Cascades are intentional.
- [ ] Decimal precision is correct.
- [ ] Timestamps use consistent timezone policy.
- [ ] Soft delete behavior is consistent.
- [ ] Enum evolution is safe.

## Migration safety

Flag migrations that:

- Add `NOT NULL` columns without backfill
- Drop columns immediately
- Rename columns without compatibility
- Rewrite large tables in one transaction
- Delete data
- Change enum values unsafely
- Add indexes in blocking ways
- Lack rollback or recovery notes

## Safer migration pattern

Use phased migration:

1. Add nullable column or new table.
2. Deploy code that dual-writes if needed.
3. Backfill in batches.
4. Verify data.
5. Switch reads.
6. Enforce constraints.
7. Remove old data later.

## Transaction review

Check writes that should be atomic:

- Payment state changes
- Inventory updates
- Account creation
- Permission changes
- Multi-table writes
- Job enqueue plus database update
- Audit log plus sensitive mutation

## Required output

```md
# Data and Migration Review

## Schema risks

## Unsafe migrations

## Missing constraints

## Missing indexes

## Transaction issues

## Backfill plan

## Rollback plan

## Tests needed
```

## Constraint

Do not make destructive schema changes without an explicit staged plan.
