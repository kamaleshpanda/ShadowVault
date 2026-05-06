# Q1. Difference between DBMS and RDBMS?

## Answer

|DBMS|RDBMS|
|---|---|
|Stores data normally|Stores data in related tables|
|No relationship between tables|Uses relationships between tables|
|Less secure|More secure|

Example:

- MySQL → RDBMS

### Interview Line

> RDBMS is a type of DBMS where data is stored in related tables using keys.

---

# Q2. Difference between DELETE, TRUNCATE, and DROP?

## Answer

| Command  | Deletes Data | Deletes Structure | WHERE Allowed |
| -------- | ------------ | ----------------- | ------------- |
| DELETE   | Yes          | No                | Yes           |
| TRUNCATE | Yes          | No                | No            |
| DROP     | Yes          | Yes               | No            |

---

# Q3. Write query to find employees with salary greater than 50000.

## Answer

``` sql
SELECT *FROM employees WHERE salary > 50000;
```

---

# Q4. Difference between WHERE and HAVING?

## Answer

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|
|Used before GROUP BY|Used after GROUP BY|
|Cannot use aggregate functions directly|Can use aggregate functions|

Example:

``` sql
SELECT city, COUNT(*)
FROM employeesGROUP 
BY city
HAVING COUNT(*) > 2;
```

---

# Q5. What does DISTINCT do?

## Answer

`DISTINCT` removes duplicate values.

Example:

```
SELECT DISTINCT city FROM employees;
```

Returns only unique city names.

---

# Q6. Difference between CHAR and VARCHAR?

## Answer

|CHAR|VARCHAR|
|---|---|
|Fixed length|Variable length|
|Wastes extra space|Saves memory|

Example:
``` sql
CHAR(20)
```
Even if `"Rahul"` is stored, remaining space is reserved.

---
# Q7. Query to find top 3 highest-paid employees.

## Answer

```
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

---

# Q8. What is PRIMARY KEY?

## Answer

> A PRIMARY KEY uniquely identifies each row in a table.

Properties:

- Unique
- Cannot contain NULL values

Example:

```
emp_id INT PRIMARY KEY
```

---

# Q9. What is FOREIGN KEY?

## Answer

> A FOREIGN KEY creates a relationship between two tables by referring to the PRIMARY KEY of another table.

Example:

```
FOREIGN KEY(dept_id)REFERENCES departments(dept_id)
```

---

# Q10. Difference between COUNT(*) and COUNT(column_name)?

## Answer

|COUNT(*)|COUNT(column_name)|
|---|---|
|Counts all rows|Counts only non-NULL values|

Example:

|salary|
|---|
|50000|
|NULL|
|60000|

```
COUNT(*) = 3COUNT(salary) = 2
```

---

# Q11. Difference between PRIMARY KEY and UNIQUE KEY?

## Answer

|PRIMARY KEY|UNIQUE KEY|
|---|---|
|Cannot contain NULL|Can contain NULL|
|Only one per table|Multiple allowed|
|Uniquely identifies rows|Prevents duplicates|

---

# Q12. What happens if WHERE salary = NULL is written?

## Answer

This will NOT work:

```
WHERE salary = NULL
```

Correct syntax:

``` sql
WHERE salary IS NULL
```

To check non-NULL:

``` sql
WHERE salary IS NOT NULL
```

---

# Q13. Query to find second highest salary.

## Answer

```
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

Another method:

```
SELECT DISTINCT salaryFROM employeesORDER BY salary DESCLIMIT 1 OFFSET 1;
```

---

# Q14. Difference between INNER JOIN and LEFT JOIN?

## Answer

|INNER JOIN|LEFT JOIN|
|---|---|
|Returns only matching rows|Returns all rows from left table|
|Non-matching rows removed|Non-matching right rows become NULL|

---

# Q15. What is Normalization?

## Answer

> Normalization is the process of organizing data to reduce redundancy and improve consistency.

Purpose:

- Avoid duplicate data
- Improve database structure

---

# Q16. Difference between UNION and UNION ALL?

## Answer

|UNION|UNION ALL|
|---|---|
|Removes duplicates|Keeps duplicates|
|Slower|Faster|

---

# Q17. What is Indexing?

## Answer

> Indexing improves the speed of data retrieval.

Works like:

> Index page in a book.

Example:

```
CREATE INDEX idx_name
ON employees(name);
```

---

# Q18. What is the default sorting order of ORDER BY?

## Answer

Default sorting order:

```
ASC
```

Ascending order.

---

# Q19. Can a table have multiple PRIMARY KEYS?

## Answer

A table can have only ONE PRIMARY KEY.

But it can be a composite primary key.

Example:

```
PRIMARY KEY(student_id, course_id)
```

---

# Q20. What is SQL query execution order?

## Answer

For query:

```
SELECT name
FROM employees
WHERE salary > 50000
ORDER BY salary;
```

Execution order:

1. FROM
2. WHERE
3. SELECT
4. ORDER BY