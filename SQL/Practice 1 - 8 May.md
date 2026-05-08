# SQL Practice Notes — Obsidian Format

## Schema Used

### users

- id
    
- name
    
- email
    
- gender
    
- date_of_birth
    
- salary
    
- created_at
    

### addresses

- id
    
- user_id
    
- street
    
- city
    
- state
    
- pin_code
    

### admin_users

- id
    
- name
    
- email
    
- gender
    
- dob
    
- salary
    

---

# Aggregate Functions

## MIN()

Used to find minimum value.

```sql
SELECT MIN(salary)
FROM users;
```

---

## MAX()

Used to find maximum value.

```sql
SELECT MAX(salary)
FROM users;
```

---

## AVG()

Used to find average value.

```sql
SELECT AVG(salary)
FROM users;
```

---

## COUNT()

Used to count rows.

```sql
SELECT COUNT(*)
FROM users;
```

---

# Basic Queries

## Find all users whose salary is greater than 50000

```sql
SELECT *
FROM users
WHERE salary > 50000;
```

---

## Find names and emails of all female users

```sql
SELECT name, email
FROM users
WHERE gender = 'female';
```

---

## Find minimum salary

```sql
SELECT MIN(salary)
FROM users;
```

---

## Find users whose salary is less than average salary

```sql
SELECT name, salary
FROM users
WHERE salary < (
    SELECT AVG(salary)
    FROM users
);
```

---

## Find the second highest salary

```sql
SELECT *
FROM users
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

---

## Find the third highest salary

```sql
SELECT *
FROM users
ORDER BY salary DESC
LIMIT 1 OFFSET 2;
```

---

## Count users having salary greater than 60000

```sql
SELECT COUNT(*)
FROM users
WHERE salary > 60000;
```

---

## Find oldest user

```sql
SELECT *
FROM users
ORDER BY date_of_birth ASC
LIMIT 1;
```

---

# GROUP BY

## Definition

`GROUP BY` is used to combine rows having same value and perform calculations on those groups.

---

## Count users by gender

```sql
SELECT gender, COUNT(*)
FROM users
GROUP BY gender;
```

---

## Find highest salary by gender

```sql
SELECT gender, MAX(salary)
FROM users
GROUP BY gender;
```

---

## Find average salary by gender

```sql
SELECT gender, AVG(salary)
FROM users
GROUP BY gender;
```

---

## Find duplicate salaries

```sql
SELECT salary, COUNT(*)
FROM users
GROUP BY salary;
```

---

# HAVING

## Definition

- `WHERE` filters rows.
    
- `HAVING` filters groups.
    

---

## Find genders having more than 1 user

```sql
SELECT gender, COUNT(*)
FROM users
GROUP BY gender
HAVING COUNT(*) > 1;
```

---

## Find salaries appearing more than once

```sql
SELECT salary, COUNT(*)
FROM users
GROUP BY salary
HAVING COUNT(*) > 1;
```

---

## Find genders whose average salary is greater than 60000

```sql
SELECT gender, AVG(salary)
FROM users
GROUP BY gender
HAVING AVG(salary) > 60000;
```

---

## HAVING without GROUP BY

```sql
SELECT COUNT(*)
FROM users
HAVING COUNT(*) > 5;
```

---

# DISTINCT

## Count distinct salaries

```sql
SELECT COUNT(DISTINCT salary)
FROM users;
```

---

## Show distinct salaries

```sql
SELECT DISTINCT salary
FROM users;
```

---

# Subqueries

## Definition

A query written inside another query is called a subquery.

---

## Find users having highest salary

```sql
SELECT *
FROM users
WHERE salary = (
    SELECT MAX(salary)
    FROM users
);
```

---

## Find users whose salary is not equal to maximum salary

```sql
SELECT *
FROM users
WHERE salary != (
    SELECT MAX(salary)
    FROM users
);
```

Alternative:

```sql
SELECT *
FROM users
WHERE salary <> (
    SELECT MAX(salary)
    FROM users
);
```

---

## Find highest female salary

```sql
SELECT MAX(salary)
FROM users
WHERE gender = 'female';
```

---

## Find female user having highest salary

```sql
SELECT name, salary
FROM users
WHERE gender = 'female'
AND salary = (
    SELECT MAX(salary)
    FROM users
    WHERE gender = 'female'
);
```

---

## Find users whose salary is greater than all male users

```sql
SELECT *
FROM users
WHERE salary > (
    SELECT MAX(salary)
    FROM users
    WHERE gender = 'male'
);
```

---

# Nested Subqueries

## Definition

A subquery inside another subquery is called a nested subquery.

---

## Find second highest salary using nested subquery

```sql
SELECT *
FROM users
WHERE salary = (
    SELECT MAX(salary)
    FROM users
    WHERE salary < (
        SELECT MAX(salary)
        FROM users
    )
);
```

---

# LIKE Operator

## Names starting with A

```sql
SELECT *
FROM users
WHERE name LIKE 'A%';
```

---

## Emails ending with gmail.com

```sql
SELECT *
FROM users
WHERE email LIKE '%gmail.com';
```

---

# Date Queries

## Find users created in year 2025

Method 1:

```sql
SELECT name
FROM users
WHERE created_at LIKE '2025%';
```

Method 2:

```sql
SELECT name
FROM users
WHERE YEAR(created_at) = 2025;
```

---

# SQL Execution Order

1. FROM
    
2. WHERE
    
3. GROUP BY
    
4. HAVING
    
5. SELECT
    
6. ORDER BY
    
7. LIMIT
    

---

# Important Concepts

## WHERE

Used to filter rows before grouping.

Example:

```sql
SELECT *
FROM users
WHERE salary > 50000;
```

---

## HAVING

Used to filter groups after grouping.

Example:

```sql
SELECT gender, COUNT(*)
FROM users
GROUP BY gender
HAVING COUNT(*) > 1;
```

---

## OFFSET

- OFFSET starts from 0.
    
- OFFSET 0 means first row.
    
- OFFSET 1 means skip first row.
    

Example:

```sql
SELECT *
FROM users
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

---

# Interview Style Practice Questions

## Q1

Find users whose salary is equal to highest salary.

```sql
SELECT *
FROM users
WHERE salary = (
    SELECT MAX(salary)
    FROM users
);
```

---

## Q2

Find users whose salary is not equal to highest salary.

```sql
SELECT *
FROM users
WHERE salary != (
    SELECT MAX(salary)
    FROM users
);
```

---

## Q3

Find second highest salary.

```sql
SELECT *
FROM users
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

---

## Q4

Find third highest salary.

```sql
SELECT *
FROM users
ORDER BY salary DESC
LIMIT 1 OFFSET 2;
```

---

## Q5

Find users whose salary is less than average salary.

```sql
SELECT *
FROM users
WHERE salary < (
    SELECT AVG(salary)
    FROM users
);
```

---

## Q6

Find count of users in each gender.

```sql
SELECT gender, COUNT(*)
FROM users
GROUP BY gender;
```

---

## Q7

Find duplicate salaries.

```sql
SELECT salary, COUNT(*)
FROM users
GROUP BY salary
HAVING COUNT(*) > 1;
```

---

## Q8

Find users whose name starts with A.

```sql
SELECT *
FROM users
WHERE name LIKE 'A%';
```

---

## Q9

Find users whose email ends with gmail.com.

```sql
SELECT *
FROM users
WHERE email LIKE '%gmail.com';
```

---

## Q10

Find users created in year 2025.

```sql
SELECT *
FROM users
WHERE YEAR(created_at) = 2025; sss
```
