## What is SQL?  
- SQL (Structured Query Language) is used to communicate with databases  
- Helps in:  
- Retrieving data  
- Filtering information  
- Working with large datasets  
- Faster and more powerful than spreadsheets  
  
---  
  
## What is a Query?  
- A query = request for data from a database  
- Written using SQL syntax  
- Acts like asking a question to the database  
  
---  
  Here is how a simple query would appear in BigQuery, a data warehouse on the Google Cloud Platform
## SQL Syntax Basics  
- SQL follows a fixed structure (syntax)  
  
```sql  
SELECT  
FROM  
WHERE  
```  
  
### Meaning:  
- `SELECT` → columns you want  
- `FROM` → table containing data  
- `WHERE` → conditions to filter data  
  
---  
  ## Basic Query Template (Detailed Explanation)

```sql
SELECT column_name
FROM dataset_name.table_name
WHERE condition;
```

### Breaking it Down

#### 1. SELECT
- Used to specify **which columns** you want to retrieve  
- Example:
  ```sql
  SELECT first_name
  ```
  This means: “Only give me the `first_name` column”

---

#### 2. FROM
- Used to specify **where the data is stored** (the table)

```sql
FROM dataset_name.table_name
```

### Why `dataset_name.table_name`?

- In systems like BigQuery, data is organized in this hierarchy:

```
Project → Dataset → Table → Columns
```

- So:
  - `dataset_name` = group of related tables  
  - `table_name` = actual table containing data  

- Example:
  ```sql
  FROM customer_data.customer_name
  ```

  Means:
  - Go to dataset: `customer_data`
  - Inside it, use table: `customer_name`

- This avoids confusion when multiple datasets have tables with the same name  

---

#### 3. WHERE
- Used to **filter rows** based on conditions  

```sql
WHERE condition
```

- Example:
  ```sql
  WHERE first_name = 'Tony'
  ```

  Means:
  - Only return rows where `first_name` is Tony  

---

## Complete Example

```sql
SELECT first_name
FROM customer_data.customer_name
WHERE first_name = 'Tony';
```

### Step-by-Step Execution (How SQL Thinks)

1. Go to table:
   ```
   customer_data.customer_name
   ```

2. Check each row:
   - Look at `first_name`

3. Apply condition:
   ```
   first_name = 'Tony'
   ```

4. Keep only matching rows  

5. Return only selected column:
   ```
   first_name
   ```

---

## Why Semicolon `;` at the End?

- The `;` means **end of query**
- It tells SQL:
  > “This query is complete, execute it”

- Important when:
  - Running multiple queries  
  - Writing scripts  

---

## Example Result

| first_name |
|-----------|
| Tony      |
| Tony      |
| Tony      |

---

## Key Understanding
- `SELECT` → what you want  
- `FROM` → where to get it  
- `WHERE` → which data to keep  
- `dataset.table` → exact location of data  
- `;` → end of instruction  

---
## Basic Query Template  
  
```sql  
SELECT column_name  
FROM table_name  
WHERE condition;  
```  
  
---  
  
## Example Query  
  
```sql  
SELECT first_name  
FROM customer_data.customer_name  
WHERE first_name = 'Tony';  
```  
  
### Explanation:  
- Selects `first_name`  
- From table `customer_data.customer_name`  
- Filters rows where name = 'Tony'  
  
---  
  
## Selecting Multiple Columns  
  
```sql  
SELECT  
customer_id,  
first_name,  
last_name  
FROM  
customer_data.customer_name  
WHERE  
first_name = 'Tony';  
```  
  
### Notes:  
- Use comma ( , ) to separate columns  
- Select only required columns to improve performance  
  
---  
  
## Multiple Conditions (WHERE)  
  
```sql  
SELECT  
ColumnA,  
ColumnB,  
ColumnC  
FROM  
table_name  
WHERE  
Condition1  
AND Condition2  
AND Condition3;  
```  
  
### Operators:  
- `AND` → all conditions must be true  
- `OR` → any condition can be true  
- `NOT` → excludes condition  
  
---  
  
## Example with Multiple Conditions  
  
```sql  
SELECT  
customer_id,  
first_name,  
last_name  
FROM  
customer_data.customer_name  
WHERE  
customer_id > 0  
AND first_name = 'Tony'  
AND last_name = 'Magnolia';  
```  
  
### Explanation:  
- Filters:  
- `customer_id > 0`  
- `first_name = 'Tony'`  
- `last_name = 'Magnolia'`  
  
---  
  
## Key Takeaways  
- SQL queries follow a structured format  
- Core clauses:  
- `SELECT`  
- `FROM`  
- `WHERE`  
- Use:  
- `,` for columns  
- `AND / OR` for conditions  
- Always select only necessary columns  
  
---  
  
## Memory Trick  
SFW → SELECT → FROM → WHERE  
  
---  
## In standard SQL (most databases like MySQL, PostgreSQL):
``` sql
SELECT *  
FROM table_name;
```
### Why BigQuery does this

Because BigQuery organizes data like:

``` 
Project → Dataset → Table
```
so :-
```sql
SELECT *
FROM project_id.dataset_name.table_name;
```


## Tags  
#SQL #DataAnalytics #Database #Queries #Learning