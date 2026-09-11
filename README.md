# SQL & DBMS Notes — Practice Scripts

Companion repository for **`SQL_DBMS_Notes.docx`** (see [`docs/`](docs/)).
Each folder below matches one chapter of the notes and contains a single,
runnable, fully-commented `.sql` file — the best working example for that
topic, cleaned up from the original lab scripts.

Every script in this repo has been executed end-to-end against a real
MySQL/MariaDB server to confirm it runs without unintended errors.

## Chapter → Script Map

| Chapter | Topic | Script |
|---|---|---|
| 2 | Understanding DBMS, RDBMS and SQL | [`02-dbms-rdbms-and-sql/02_dbms_rdbms_sql_basics.sql`](02-dbms-rdbms-and-sql/02_dbms_rdbms_sql_basics.sql) |
| 4 | Database, Schema, Table, Row and Column | [`04-database-schema-table-column/04_database_schema_table_demo.sql`](04-database-schema-table-column/04_database_schema_table_demo.sql) |
| 6 | SQL Data Types | [`06-sql-data-types/06_sql_data_types_showcase.sql`](06-sql-data-types/06_sql_data_types_showcase.sql) |
| 7 | Modifying Database Structure | [`07-modifying-database-structure/07_alter_table_operations.sql`](07-modifying-database-structure/07_alter_table_operations.sql) |
| 8 | Keys and Constraints | [`08-keys-and-constraints/08_keys_and_constraints_demo.sql`](08-keys-and-constraints/08_keys_and_constraints_demo.sql) |
| 9 | DML: Managing Data (INSERT, UPDATE, DELETE) | [`09-dml-managing-data/09_insert_update_delete_demo.sql`](09-dml-managing-data/09_insert_update_delete_demo.sql) |

> Chapters 1, 3, and 5 (Data Fundamentals, SQL Command Categories, and
> Installing MySQL) are conceptual / setup chapters with no dedicated
> practice script.

## How to Run

1. Open **MySQL Workbench** (see Chapter 5 of the notes if it isn't installed yet).
2. Open any script from the table above and run it top to bottom (⚡ **Execute**).
3. Each script creates and uses its own database, so scripts are independent
   of one another and can be run in any order.

### A note on Chapter 8

`08_keys_and_constraints_demo.sql` intentionally includes several `INSERT`
statements that **are supposed to fail** (labelled `TEST 2` through `TEST 7`)
to demonstrate each constraint being enforced. This is expected behaviour,
not a bug:

- Running it in **MySQL Workbench** — each statement runs independently, so
  you'll see the failing statements flagged in red while the rest of the
  script continues normally.
- Running it via the **command line** (`mysql -u root -p < script.sql`) —
  the client stops at the first error by default. Add the `--force` flag to
  continue past the intentional failures:
  ```bash
  mysql -u root -p --force < 08-keys-and-constraints/08_keys_and_constraints_demo.sql
  ```

## Repository Structure

```
sql-dbms-notes/
├── README.md
├── docs/
│   └── SQL_DBMS_Notes.docx        <- the full course notes
├── 02-dbms-rdbms-and-sql/
├── 04-database-schema-table-column/
├── 06-sql-data-types/
├── 07-modifying-database-structure/
├── 08-keys-and-constraints/
└── 09-dml-managing-data/
```

## Source

These scripts were rewritten, corrected, and commented from a larger set of
personal practice labs, consolidated to one clean example per notes chapter.
