# SQL Cheat Sheet — Google Cybersecurity Certificate (Course 4)

Quick reference for SQL commands covered in the Linux and SQL course, based on queries used against the `organization` database (`machines`, `employees`, `log_in_attempts` tables).

## Basic query structure

```sql
SELECT column1, column2
FROM table_name;
```

- `SELECT` — which columns to return
- `FROM` — which table to pull from
- `;` — ends the command
- `SELECT *` returns all columns
- Table and column names are case-sensitive in MySQL/MariaDB

## Explore table structure

```sql
DESCRIBE machines;
DESCRIBE employees;
```

Shows column names (`Field`) and data types (`Type`) without returning row data.

## Sorting results

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date;
```

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;
```

- Sorts ascending by default
- Multiple columns sort in the order listed (first by date, then by time within matching dates)

## Filtering with WHERE

```sql
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';
```

- Strings go in single quotes
- Column names are never quoted
- Numbers and booleans (`TRUE`/`FALSE`) are not quoted

## Comparison operators

```sql
WHERE login_date > '2023-01-15'
WHERE login_date >= '2023-01-15'
WHERE login_date < '2023-01-15'
WHERE login_date <= '2023-01-15'
WHERE login_time = '09:30:00'
```

## BETWEEN

```sql
SELECT *
FROM log_in_attempts
WHERE login_date BETWEEN '2023-02-01' AND '2023-02-07';
```

Inclusive of both start and end values.

## LIKE and wildcards

```sql
WHERE office LIKE 'South%'   -- starts with South
WHERE office LIKE '%South'   -- ends with South
WHERE office LIKE '%South%'  -- contains South anywhere
```

`%` matches any number of characters, including zero.

## Combining conditions

```sql
-- AND: both conditions must be true
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;

-- OR: either condition can be true
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';

-- NOT: excludes matches
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

Note both sides of an OR need the full condition even on the same column:

```sql
WHERE department = 'Finance' OR department = 'Sales';
```

## Joins

```sql
-- INNER JOIN: only rows that match in both tables
SELECT *
FROM machines
INNER JOIN employees ON machines.device_id = employees.device_id;

-- LEFT JOIN: all rows from the left table, NULL where no match
SELECT *
FROM machines
LEFT JOIN employees ON machines.device_id = employees.device_id;

-- RIGHT JOIN: all rows from the right table, NULL where no match
SELECT *
FROM machines
RIGHT JOIN employees ON machines.device_id = employees.device_id;
```

- `Table.Column` dot notation avoids ambiguity when both tables share a column name
- Left table = listed after `FROM`
- Right table = listed after `JOIN`
- Most analysts default to `LEFT JOIN` and just reorder tables instead of using `RIGHT JOIN`

## Quick troubleshooting

- Forgot the semicolon → shell hangs on `->` prompt, type `;` and press Enter
- `0 rows in set` → check spelling of column/table names
- String values must be in single quotes, column names never are
- `TRUE`/`FALSE` are booleans, not strings — no quotes

— Reference sheet compiled while completing the Google Cybersecurity Certificate program.