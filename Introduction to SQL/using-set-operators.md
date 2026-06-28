# Using the Set Operators – Hands-on Assignment

## 1. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job, for departments 10, 20, and 30, giving each column an appropriate heading.

```sql
SELECT job,
       SUM(DECODE(department_id,10,salary)) AS Dept10,
       SUM(DECODE(department_id,20,salary)) AS Dept20,
       SUM(DECODE(department_id,30,salary)) AS Dept30,
       SUM(salary) AS Total
FROM employees
WHERE department_id IN (10,20,30)
GROUP BY job;
```

---

## 2. Using the SET operator, display the DEPTNO, SUM(SAL) for each department, JOB, SUM(SAL) for each job, and Total Salary.

```sql
SELECT TO_CHAR(department_id) AS Department,
       NULL AS Job,
       SUM(salary) AS Total_Salary
FROM employees
GROUP BY department_id

UNION

SELECT NULL,
       job_id,
       SUM(salary)
FROM employees
GROUP BY job_id

UNION

SELECT 'TOTAL',
       NULL,
       SUM(salary)
FROM employees;
```

---

## 3. Using the SET operator, display the JOB and DEPTNO of employees working in departments 20, 10, and 30 in that order.

```sql
SELECT job_id, department_id
FROM employees
WHERE department_id = 20

UNION ALL

SELECT job_id, department_id
FROM employees
WHERE department_id = 10

UNION ALL

SELECT job_id, department_id
FROM employees
WHERE department_id = 30;
```
