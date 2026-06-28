
# Reporting Aggregated Data Using the Group Functions – Hands-on Assignment

## 1. Find the highest, lowest, sum, and average salary of all employees. Label the columns Maximum, Minimum, Sum, and Average, respectively.

```sql
SELECT MAX(salary) AS Maximum,
       MIN(salary) AS Minimum,
       SUM(salary) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees;
```

---

## 2. Round your results to the nearest whole number.

```sql
SELECT ROUND(MAX(salary)) AS Maximum,
       ROUND(MIN(salary)) AS Minimum,
       ROUND(SUM(salary)) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees;
```

---

## 3. Modify the above query to display the minimum, maximum, sum, and average salary for each job type.

```sql
SELECT job_id,
       MIN(salary) AS Minimum,
       MAX(salary) AS Maximum,
       SUM(salary) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees
GROUP BY job_id;
```

---

## 4. Write a query to display the number of people with the same job.

```sql
SELECT job_id,
       COUNT(*) AS Number_of_People
FROM employees
GROUP BY job_id;
```

---

## 5. Determine the number of managers without listing them. Label the column Number of Managers.

```sql
SELECT COUNT(DISTINCT manager_id) AS "Number of Managers"
FROM employees;
```

---

## 6. Find the difference between the highest and lowest salaries. Label the column DIFFERENCE.

```sql
SELECT MAX(salary) - MIN(salary) AS DIFFERENCE
FROM employees;
```

---

## 7. Create a report to display the manager number and the salary of the lowest-paid employee for that manager. Exclude anyone whose manager is not known. Exclude any groups where the minimum salary is $2000 or less. Sort the output in descending order of salary.

```sql
SELECT manager_id,
       MIN(salary) AS Lowest_Salary
FROM employees
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) > 2000
ORDER BY Lowest_Salary DESC;
```

---

## 8. Create a query to display the total number of employees and, of that total, the number of employees hired in 1980, 1981, and 1982. Create appropriate column headings.

```sql
SELECT COUNT(*) AS Total_Employees,
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1980 THEN 1 ELSE 0 END) AS "1980",
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1981 THEN 1 ELSE 0 END) AS "1981",
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1982 THEN 1 ELSE 0 END) AS "1982"
FROM employees;
```
