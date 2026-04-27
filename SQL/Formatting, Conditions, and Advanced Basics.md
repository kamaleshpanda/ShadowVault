## Capitalization, Indentation, and Semicolons

- SQL is **not case-sensitive** → you can write in lowercase  
- But best practice:
  - Use **UPPERCASE** for keywords (`SELECT`, `FROM`, `WHERE`)
  - Use **indentation** for readability  

```sql
SELECT field1
FROM table
WHERE field1 = condition;
```

### Semicolon `;`
- Acts as a **statement terminator**
- Part of ANSI SQL standard  
- Not always required, but **recommended**

---

## WHERE Conditions

- `WHERE` filters data based on conditions  

### Exact match
```sql
WHERE field1 = 'Chavez';
```

### Pattern match using LIKE
```sql
WHERE field1 LIKE 'Ch%';
```

### Key points:
- `LIKE` → used for pattern matching  
- `%` → wildcard (matches any number of characters)  
  - `'Ch%'` → Chavez, Chen, etc.  
  - Refer [[#SQL Wildcards]]

---

## Selecting All Columns

### Using `*`
```sql
SELECT *
FROM table;
```

### Notes:
- `*` means **select all columns**
- Use carefully:
  - Can slow down queries  
  - Returns unnecessary data if table is large  

---

## Comments in SQL

- Used to explain queries  

### Single-line comment
```sql
-- This is a comment
```

### Inline comment
```sql
SELECT
    field1 -- last name column
FROM
    table;
```

### Multi-line comment
```sql
/* This is a
multi-line comment */
```

### Why comments matter:
- Improve readability  
- Help others understand your query  
- Useful for future reference  

---

## Example with Comments

```sql
-- Pull basic customer information
SELECT
    customer_id, -- unique ID
    first_name,  -- first name
    last_name    -- last name
FROM
    customer_data.customer_name;
```

---

## Aliases (AS)

- Used to give temporary names to:
  - Columns  
  - Tables  

```sql
SELECT 
    my_table_alias.actual_column_name AS my_column_alias
FROM
    actual_table_name AS my_table_alias;
```

### Key points:
- `AS` assigns alias  
- Works only during the query  
- Does not change actual table/column name  

---

## Practical Example (Employee Data)

### Step 1: Get all data
```sql
SELECT *
FROM Employee;
```

---

### Step 2: Filter by job code
```sql
SELECT *
FROM Employee
WHERE jobCode = 'SFI';
```

---

### Step 3: Advanced filtering

Goal:
- Salary ≤ 30000  
- Exclude interns (`INT`)  

```sql
SELECT *
FROM Employee
WHERE jobCode <> 'INT' -- jobcode is not equal to interns
  AND salary <= 30000;
```

### Key operators:
- `<>` → not equal  
- `AND` → both conditions must be true  

---

## Key Takeaways

- SQL formatting improves readability:
  - Capitalization  
  - Indentation  
- `WHERE` filters data  
- `LIKE` + `%` enables pattern matching  
- `SELECT *` should be used carefully  
- Comments help document queries  
- Aliases simplify complex queries  

---

## Summary

SQL is not just about writing queries—it’s about writing **clear, readable, and efficient queries**.  
As queries grow complex, formatting, comments, and aliases become essential tools.

---
# SQL Wildcards

Wildcards are used with the `LIKE` operator to search for patterns in data.


---

## Main Wildcards

### 1. Percent `%`
- Matches **zero, one, or many characters**

```sql
WHERE name LIKE 'A%'
```
- Starts with A → Amit, Ankit  

```sql
WHERE name LIKE '%A'
```
- Ends with A → Sita, Rama  

```sql
WHERE name LIKE '%mit%'
```
- Contains "mit" → Amitabh  

---

### 2. Underscore `_`
- Matches **exactly one character**

```sql
WHERE name LIKE '_mit'
```
- 4-letter names ending with "mit" → Amit  

```sql
WHERE name LIKE 'A_it'
```
- A + any one letter + it → Amit  

---

## Advanced / Less Common Wildcards

> These depend on the database (not universal)

---

### 3. Square Brackets `[ ]` (SQL Server)
- Match **any one character inside brackets**

```sql
WHERE name LIKE '[ABC]mit'
```
- Amit, Bmit, Cmit  

---

### 4. Range `[a-z]` (SQL Server)
```sql
WHERE name LIKE '[A-C]mit'
```
- Amit, Bmit, Cmit  

---

### 5. Negation `[ ^ ]` (SQL Server)
```sql
WHERE name LIKE '[^A]mit'
```
- Not starting with A  

---

### 6. NOT LIKE
- Excludes pattern

```sql
WHERE name NOT LIKE 'A%'
```
- Names not starting with A  

---

## Important Notes

- `%` and `_` → **work in almost all SQL databases**  
- `[ ]` → mainly in **SQL Server**, not in MySQL/PostgreSQL/BigQuery  
- BigQuery uses:
  - `LIKE` (basic)
  - `REGEXP_CONTAINS()` for advanced patterns  

---

## Quick Comparison

| Wildcard | Meaning                     | Example        |
|----------|---------------------------|----------------|
| `%`      | Any number of characters  | 'A%'           |
| `_`      | Exactly one character     | 'A_'           |
| `[ABC]`  | Any one of A, B, C        | '[ABC]mit'     |
| `[A-Z]`  | Range                     | '[A-Z]mit'     |
| `[^A]`   | Not A                     | '[^A]mit'      |

---

## Pro Tip

- Use `%` → most common  
- Use `_` → for fixed-length patterns  
- Use regex (advanced cases) instead of complex wildcards  

---
## Tags
#SQL #DataAnalytics #QueryWriting #Database #Learning