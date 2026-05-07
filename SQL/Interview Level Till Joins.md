#  SQL Interview Questions (Pre-JOIN Level Only)

>  Do NOT use JOIN  
> Focus: SELECT, WHERE, GROUP BY, HAVING, ORDER BY, LIMIT, DML

---

# SECTION 1: Filtering & Logic (Tricky)

1. Find employees whose salary is between 30,000 and 70,000 but NOT equal to 50,000.

2. Find employees whose name starts with 'A' and ends with 'n'.

3. Find employees whose salary is not in (30000, 40000, 50000).

4. Show employees whose age is either 25, 30, or 35.

5. Find employees whose name has exactly 5 characters.

---

#  SECTION 2: Sorting & Ranking Logic

6. Show top 3 highest salaries (without duplicates).

7. Show the second highest salary (IMPORTANT question).

8. List employees sorted by salary ascending, and if same salary, sort by name descending.

9. Show bottom 5 lowest-paid employees.

10. Find employees whose salary is higher than 80% of employees.

---

#  SECTION 3: Aggregation (Concept-Based)

11. Find total salary of all employees.

12. Find average salary excluding employees earning less than 20,000.

13. Count employees whose salary is above average.

14. Find difference between highest and lowest salary.

---

#  SECTION 4: GROUP BY + HAVING (Very Important)

15. Count employees in each department.

16. Find departments where average salary is greater than 60,000.

17. Find departments having more than 5 employees.

18. Find cities where total salary exceeds 5,00,000.

---

#  SECTION 5: Mixed (Interview Traps)

19. Find employees whose salary is greater than the average salary.

20. Delete employees whose salary is below company average salary.

---

#  Tips

- Use:
  - WHERE → row filtering
  - HAVING → group filtering
- Remember:
  - Subqueries may be required for some questions
- Avoid:
  - Writing English (like "is greater than")

---

==select salary 
from employees 
order by salary desc 
limit 1 offset (n-1) ; do late==