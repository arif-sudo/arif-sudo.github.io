---
title: "SQL Intermediate"
layout: post
---

## Complex joins
### GROUP BY clause
The `GROUP BY` clause is used with the SELECT statement to make a group of rows based on the values of a specific column or expression. The SQL AGGREGATE function can be used to get summary information for every group and these are applied to an individual group
The following query displays number of employees work in each department
```sql
SELECT department_id "Department Code", 
COUNT(*) "No of Employees" 
FROM employees 
GROUP BY department_id; 
```

The following query displays total salary paid to employees work in each department
```sql
SELECT department_id, SUM(salary) 
FROM  employees 
GROUP BY  department_id;
```

The following query displays the department code, job id, total salary paid to employees group by department_id, job_id
```sql
SELECT department_id "Department Code", job_id, 
SUM(salary) "Total Salary" 
FROM  employees 
GROUP BY  department_id, job_id;
```

The following query displays the department id, number of employees of those groups that have more than 2 employees
```sql
SELECT department_id, count(*) "No. of Employee" 
FROM employees 
GROUP BY department_id 
HAVING count(*)>2;
```

### Join with Aggregation
```sql
SELECT departments.department_id, departments.department_name, COUNT(employees.employee_id) AS employee_count
FROM departments
LEFT JOIN employees ON departments.department_id = employees.department_id
GROUP BY departments.department_id, departments.department_name;
```

---

## Unions  
### Rules for combining two or more queries using UNION
1. number of columns and order of columns of all queries must be same
2. the data types of the columns on involving table in each query must be same or compatible
3. usually returned column names are taken from the first query

> By default the UNION behaves like UNION [DISTINCT] , i.e. eliminated the duplicate rows
> However, using ALL keyword with UNION returns all rows, including duplicates

### Difference between Join and Union
> The columns of joining tables may be different in JOIN but in UNION the number of columns and order of columns of all queries must be same

Union of 2 tables
```sql
SELECT employee_id, employee_name FROM employees
UNION
SELECT vendor_id, vendor_name FROM vendors;
```

Union ALL with WHERE
```sql
SELECT prod_code,prod_name,com_name
FROM product 
WHERE life>6
UNION ALL
SELECT prod_code,prod_name,com_name
FROM purchase 
WHERE pur_qty>10
```

Union a table to itself
```sql
SELECT prod_code,prod_name,com_name
FROM purchase 
WHERE pur_qty>6
UNION ALL
SELECT prod_code,prod_name,com_name
FROM purchase 
WHERE pur_amount>100000
```
Union with different column names  
In the following example, the two queries have been set using two different criteria and different columns  
The different columns in two statements are 'life' and 'pur_qty'. But as the data type are same for both the columns so, result has displayed. Usually returned column names are taken from the first query  
```sql
SELECT prod_code,prod_name,life
FROM product
WHERE life>6
UNION
SELECT prod_code,prod_name,pur_qty
FROM purchase
WHERE pur_qty<20
```

Union with Inner Join
```sql
SELECT product.prod_code,product.prod_name,
purchase.pur_qty, purchase.pur_amount  
FROM product
INNER JOIN purchase  
ON product.prod_code = purchase.prod_code
UNION
SELECT product.prod_code,product.prod_name,
purchase.pur_qty, purchase.pur_amount  
FROM product
INNER JOIN purchase  
ON product.prod_name = purchase.prod_name;
```

Union All with Order By
```sql
SELECT employee_id, employee_name FROM employees
UNION ALL
SELECT vendor_id, vendor_name FROM vendors
ORDER BY 2; -- Order by the second column
```

## Sub-queries
A subquery may occur in :
- A SELECT clause
- A FROM clause
- A WHERE clause
The subquery can be nested inside a SELECT, INSERT, UPDATE, or DELETE statement or inside another subquery

### You can combine two queries by placing one query inside the other
```sql
SELECT a.studentid, a.name, b.total_marks
FROM student a, marks b
WHERE a.studentid = b.studentid AND b.total_marks >
(SELECT total_marks
FROM marks
WHERE studentid =  'V002');
```
