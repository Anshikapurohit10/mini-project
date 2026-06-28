# Restricting and Sorting Data - Answers

## 1. Display the Ename, Sal, Comm from Emp table who earn commission and sort the records in descending order of Salary and Comm. Use column's numeric position in the ORDER BY clause.

```sql
SELECT ENAME, SAL, COMM
FROM EMP
WHERE COMM IS NOT NULL
ORDER BY 2 DESC, 3 DESC;
```

---

## 2. The HR department needs a query to display all unique job codes from the EMP table.

```sql
SELECT DISTINCT JOB
FROM EMP;
```

---

## 3. The HR department wants more descriptive column headings for its report on employees. Name the column headings Emp #, Employee, Job, and Hire Date, respectively by giving Column Alias.

```sql
SELECT EMPNO AS "Emp #",
       ENAME AS "Employee",
       JOB AS "Job",
       HIREDATE AS "Hire Date"
FROM EMP;
```

---

## 4. The HR department has requested a report of all employees and their job IDs. Display the last name concatenated with the job ID (separated by a comma and space) and name the column Employee and Title by giving Column Alias.

```sql
SELECT ENAME || ', ' || JOB AS "Employee and Title"
FROM EMP;
```

---

## 5. To familiarize yourself with the data in the EMP table, create a query to display all the data from that table. Separate each column output by a comma. ENAME, JOB, HIREDATE, MGR. Name the column title THE_OUTPUT.

```sql
SELECT ENAME || ',' || JOB || ',' || HIREDATE || ',' || MGR AS THE_OUTPUT
FROM EMP;
```

---

## 6. Create a report to display the ename, job and hiredate for the employees name is SCOTT or TURNER. Order the query in ascending order by hiredate.

```sql
SELECT ENAME, JOB, HIREDATE
FROM EMP
WHERE ENAME IN ('SCOTT', 'TURNER')
ORDER BY HIREDATE ASC;
```

---

## 7. Display the ename and department number of all employees in departments 20 or 30 in ascending alphabetical order by ename.

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE DEPTNO IN (20, 30)
ORDER BY ENAME;
```

---

## 8. Modify the previous query to display the last name and salary of employees who earn between 2000 and 3000 and are in department 20 or 30. Label the columns Employee and Monthly Salary, respectively by giving Column Alias.

```sql
SELECT ENAME AS "Employee",
       SAL AS "Monthly Salary"
FROM EMP
WHERE SAL BETWEEN 2000 AND 3000
  AND DEPTNO IN (20, 30);
```

---

## 9. The HR department needs a report that displays the last name and hire date for all employees who were hired in 1981.

```sql
SELECT ENAME, HIREDATE
FROM EMP
WHERE HIREDATE BETWEEN '01-JAN-81' AND '31-DEC-81';
```

---

## 10. Display the Ename, Sal of employees who earn more than an amount the user specifies after a Prompt.

```sql
ACCEPT AMT PROMPT 'Enter Salary : '

SELECT ENAME, SAL
FROM EMP
WHERE SAL > &AMT;
```

---

## 11. Create a report to display the last name and job title of all employees who do not have a manager.

```sql
SELECT ENAME, JOB
FROM EMP
WHERE MGR IS NULL;
```

---

## 12. Create a query that prompts the user for Manager ID and generate EMPNO, ENAME, SAL, DEPTNO. The user should have the ability to sort the records on a selected Column.

```sql
ACCEPT MID PROMPT 'Enter Manager ID : '
ACCEPT COL PROMPT 'Enter Column Name : '

SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MID
ORDER BY &COL;
```

---

## 13. The HR department wants to run reports based on a manager. Create a query that prompts the user for a MGR and generates the empno, ename, salary, and department for that manager's employees. The HR department wants the ability to sort the report on a selected column.

```sql
ACCEPT MID PROMPT 'Enter Manager ID : '
ACCEPT COL PROMPT 'Enter Column Name : '

SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MID
ORDER BY &COL;
```

---

## 14. Display all employee last names in which the third letter of the name is A.

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '__A%';
```

---

## 15. Display the last name of all employees who have both an A and an S in their ename.

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '%A%'
  AND ENAME LIKE '%S%';
```

---

## 16. Display the Ename, Job, Sal for all employees whose jobs are CLERK and whose salary is in 800 or 950 or 1300.

```sql
SELECT ENAME, JOB, SAL
FROM EMP
WHERE JOB = 'CLERK'
  AND SAL IN (800, 950, 1300);
```
