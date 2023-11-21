---
title: "SQL Basics"
layout: post
---

## Simple queries
### Most used queries
Selecting All Columns from a Table
```sql
SELECT * FROM employees;
```

Selecting Specific Columns
```sql
SELECT employee_id, first_name, last_name FROM employees;
```

Filtering Rows with WHERE Clause
```sql
SELECT * FROM employees WHERE department_id = 10;
```

### Additional keywords
`DISTINCT` keyword is used in a `SELECT` statement to eliminate duplicate rows from the result set
```sql
SELECT DISTINCT department_id FROM employees;
```

You can also use DISTINCT with multiple columns to retrieve unique combinations of values
```sql
SELECT DISTINCT department_id, job_id FROM employees;
```

`ORDER BY` clause is used to sort the result set of a query in either ascending `ASC` or descending `DESC` order based on one or more columns
```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY last_name, first_name;
```
In this example, the result set will be sorted first by the "last_name" column in ascending order and then by the "first_name" column in ascending order. You can specify multiple columns in the `ORDER BY` clause, and the sorting is applied in the order the columns are listed
```sql
-- Sorting by salary in descending order
SELECT employee_id, first_name, last_name, salary
FROM employees
ORDER BY salary DESC;
```
> It's important to note that `ORDER BY` is not only limited to sorting numeric or date columns; it can also be used to sort text columns alphabetically.

## Conversion
In SQL, conversion functions allow you to convert data from one data type to another

### 1. TO_CHAR
```sql
-- Convert a date to a string with a specific format
SELECT TO_CHAR(hire_date, 'DD-MON-YYYY') AS formatted_date FROM employees;

-- Convert a number to a string with a specific format
SELECT TO_CHAR(salary, '999,999.99') AS formatted_salary FROM employees;
```
Original Salary: 1234567.89
Formatted Salary: 1,234,567.89

Original Salary: 98765.43
Formatted Salary: 98,765.43

### 2. TO_DATE
```sql
-- Convert a string to a date with a specific format
SELECT TO_DATE('21-NOV-2023', 'DD-MON-YYYY') AS converted_date FROM dual;
```

### 3. TO_NUMBER
```sql
-- Convert a string to a number
SELECT TO_NUMBER('12345') AS numeric_value FROM dual;
```

### 4. CAST and CONVERT
```sql
SELECT CAST('2022-01-15' AS DATE)
SELECT CAST(25.65 AS int);

SELECT CONVERT(int, 25.65);
```

EXPLICIT and IMPLICIT CAST
```sql
-- Implicit casting (automatic conversion)
SELECT salary + 500 AS increased_salary FROM employees;

-- Explicit casting (using CAST)
SELECT CAST('123' AS int) + 5 AS result FROM dual;
```

### 5. NVL, NVL2, COALESCE
These functions are used to handle NULL values and can implicitly perform type conversions.
```sql
-- Using NVL to convert NULL to a default value
SELECT NVL(column_name, 'Default') AS result
FROM table_name;

-- Using NVL2 to provide different results based on whether an expression is NULL or not NULL
SELECT 
  employee_id,
  NVL2(manager_id, 'Has Manager', 'No Manager') AS manager_status
FROM employees;


-- Using COALESCE to return the first non-NULL value
SELECT COALESCE(column1, column2, column3, 'No Value') AS result
FROM table_name;
```

### 6. CASE Expression
The CASE expression can be used for conditional conversions.
```sql
SELECT 
  CASE 
    WHEN age >= 18 THEN 'Adult'
    ELSE 'Minor'
  END AS age_group
FROM persons;
```

### 7. EXTRACT
The `EXTRACT` function in Oracle SQL is used to extract a specific component
```sql
SELECT 
  hire_date,
  EXTRACT(YEAR FROM hire_date) AS hire_year,
  EXTRACT(MONTH FROM hire_date) AS hire_month,
  EXTRACT(DAY FROM hire_date) AS hire_day
FROM employees;
```

## Relationships  
There are 4 mian JOIN's in SQL
They are INNER, LEFT, RIGHT and FULL JOIN
1. INNER JOIN
An `INNER JOIN` returns only the rows that have matching values in both tables

```sql
SELECT employees.employee_id, employees.first_name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

2. LEFT JOIN
A `LEFT JOIN` returns all rows from the left table and the matched rows from the right table. If there is no match, the result will contain NULL values for columns from the right table
```sql
SELECT employees.employee_id, employees.first_name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;
```

3. FULL JOIN
A `FULL JOIN`, also known as a FULL OUTER JOIN, is a type of join operation in SQL that returns all rows when there is a match in either the left (first) table or the right (second) table. If there is no match, the result will contain NULL values for columns from the table without a match
```sql
SELECT *
FROM table1
FULL JOIN table2
ON table1.column_name = table2.column_name;
```

## Aggregators
* Counting Rows
```sql
SELECT COUNT(*) FROM employees;
```

* Summing values
```sql
SELECT department_id, SUM(salary) as total_salary
FROM employees
GROUP BY department_id;
```

* Finding Maximum and Minimum Values
```sql
SELECT MAX(salary) as max_salary, MIN(salary) as min_salary
FROM employees;
```

* Average
```sql
SELECT AVG(salary) as average_salary
FROM employees;
```
{% comment %}
Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
{% endcomment %}


