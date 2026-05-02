# SQL Complete Notes (Beginner → Pre-JOIN)

---

# 1. What is SQL?

SQL (Structured Query Language) is used to:
- Store data
- Retrieve data
- Modify data
- Manage databases

---

#  2. Basic Structure

## Table Example:
students(id, name, age, marks)

| id | name | age | marks |
|----|------|-----|-------|

---

#  3. SELECT Statement

## Syntax:
SELECT column_name FROM table_name;

## Examples:

### All columns
SELECT * FROM students;

### Specific columns
SELECT name, marks FROM students;

---

#  4. WHERE Clause (Filtering)

## Syntax:
SELECT * FROM students WHERE condition;

## Operators:
- =  (equal)
- >  (greater than)
- <  (less than)
- >=, <=
- != (not equal)

## Examples:

SELECT * FROM students WHERE marks > 75;

SELECT * FROM students WHERE age < 20;

---

#  5. Logical Operators

- AND → both conditions true
- OR → any condition true
- NOT → opposite

## Example:

SELECT * FROM students
WHERE marks > 70 AND age < 20;

---

# 6. LIKE (Pattern Matching)

## Syntax:
SELECT * FROM students WHERE name LIKE 'pattern';

## Symbols:
- % → any number of characters
- _ → single character

## Examples:

SELECT * FROM students WHERE name LIKE 'A%';   -- starts with A
SELECT * FROM students WHERE name LIKE '%a';   -- ends with a

---

# 7. BETWEEN

## Syntax:
SELECT * FROM students WHERE column BETWEEN x AND y;

## Example:
SELECT * FROM students WHERE marks BETWEEN 60 AND 80;

---

#  8. IN Operator

## Example:
SELECT * FROM students WHERE age IN (18, 19, 20);

---

# 9. ORDER BY (Sorting)

## Syntax:
SELECT * FROM students ORDER BY column ASC/DESC;

## Examples:

SELECT * FROM students ORDER BY marks ASC;
SELECT * FROM students ORDER BY marks DESC;

---

# 10. DISTINCT

## Removes duplicates

SELECT DISTINCT age FROM students;

---

#  11. Aggregate Functions

| Function | Meaning |
|--------|--------|
| COUNT() | Count rows |
| SUM() | Total |
| AVG() | Average |
| MAX() | Maximum |
| MIN() | Minimum |

## Examples:

SELECT COUNT(*) FROM students;

SELECT AVG(marks) FROM students;

SELECT MAX(marks) FROM students;

---

#  12. GROUP BY

## Used with aggregate functions

## Syntax:
SELECT column, AGG_FUNC(column)
FROM table
GROUP BY column;

## Example:

SELECT department, AVG(marks)
FROM students
GROUP BY department;

---

#  13. HAVING

## Used to filter grouped data

## Syntax:
SELECT column, AGG_FUNC(column)
FROM table
GROUP BY column
HAVING condition;

## Example:

SELECT department, AVG(marks)
FROM students
GROUP BY department
HAVING AVG(marks) > 75;

---

#  14. CREATE TABLE

## Syntax:

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(20),
    salary INT
);

---

#  15. INSERT

## Syntax:

INSERT INTO employees (id, name, salary)
VALUES (1, 'Rahul', 30000);

---

#  16. UPDATE

## Syntax:

UPDATE employees
SET salary = salary * 1.10;

---

#  17. DELETE

## Syntax:

DELETE FROM employees
WHERE salary < 20000;

---

#  COMMON MISTAKES

❌ Using English:
marks is greater than 70  
✔ marks > 70

❌ Wrong function:
average()  
✔ AVG()

❌ Missing brackets:
MAX marks  
✔ MAX(marks)

❌ LIKE mistake:
name = 'A%'  
✔ name LIKE 'A%'

---

#  SUMMARY

Before JOIN, you must know:

- SELECT ✔
- WHERE ✔
- LIKE ✔
- ORDER BY ✔
- DISTINCT ✔
- Aggregate functions ✔
- GROUP BY ✔
- HAVING ✔
- INSERT / UPDATE / DELETE ✔

---

#  PRACTICE QUESTIONS

## Easy

1. Show all studentsn
2. Show names and marks
3. Students with marks > 80
4. Students with age < 20

---

## Medium

5. Students whose name starts with 'S'
6. Students with marks between 50 and 90
7. Sort students by marks descending
8. Show distinct ages

---

## Aggregation

9. Find average marks
10. Find maximum marks
11. Count total students

---

## GROUP BY

12. Average marks per department
13. Departments with avg marks > 70

---

## DML

14. Create employee table
15. Insert 2 records
16. Increase salary by 20%
17. Delete employees with salary < 25000

---
#  Additional Practice Questions (Pre-JOIN Level)

---

## 18. Find employees with salary > 50000

### Query:
SELECT * 
FROM employees
WHERE salary > 50000;

### Explanation:
- Filters rows where salary is greater than 50,000

---

## 19. Show average salary per department

### Query:
SELECT department, AVG(salary)
FROM employees
GROUP BY department;

### Explanation:
- Groups employees by department
- Calculates average salary in each department

---

## 20. List top 5 highest-paid employees

### Query:
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 5;

### Explanation:
- Sorts salaries in descending order
- LIMIT 5 returns top 5 rows

---

##  21. Count employees in each city

### Query:
SELECT city, COUNT(*)
FROM employees
GROUP BY city;

### Explanation:
- Groups by city
- Counts employees in each city

---

##  22. Find departments with more than 10 employees

### Query:
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;

### Explanation:
- GROUP BY department
- HAVING filters groups with more than 10 employees

---

# Important Notes

- GROUP BY → used before aggregation
- HAVING → used after aggregation
- ORDER BY → used for sorting
- LIMIT → restrict number of rows

---

# Mini Revision Trick

| Task | Keyword |
|------|--------|
| Filter rows | WHERE |
| Filter groups | HAVING |
| Group data | GROUP BY |
| Sort | ORDER BY |
| Top N | LIMIT |

---

# Challenge (Try Yourself)

1. Show top 3 lowest salaries  
2. Count employees per department where salary > 30000  
3. Find average salary of employees in each city where avg > 40000  
