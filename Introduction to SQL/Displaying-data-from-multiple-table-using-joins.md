# SQL Joins – Hands-on Assignments

## 1. Natural Join
**Question:**  
Write a query for the HR department to produce the addresses of all the departments. Use the EMP and DEPT tables. Show the **EMPNO, ENAME, SAL, DNAME, and LOC** in the output. Use a **NATURAL JOIN** to produce the results.

```sql
SELECT EMPNO, ENAME, SAL, DNAME, LOC
FROM EMP
NATURAL JOIN DEPT;
```

---

## 2. Equi Join
**Question:**  
Write a query to display the **JOB, MGR, SAL, COMM, DNAME** of employees whose **JOB** is **SALESMAN**.

```sql
SELECT E.JOB, E.MGR, E.SAL, E.COMM, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.JOB = 'SALESMAN';
```

---

## 3. Equi Join
**Question:**  
Display the **ENAME, JOB, DEPTNO, DNAME** for all employees who work in **DALLAS**.

```sql
SELECT E.ENAME, E.JOB, E.DEPTNO, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND D.LOC = 'DALLAS';
```

---

## 4. Self Join
**Question:**  
Create a report to display employees' name and employee number along with their manager's name and manager number. Label the columns **Employee, Emp#, Manager, Mgr#** respectively.

```sql
SELECT
    E.ENAME AS Employee,
    E.EMPNO AS "Emp#",
    M.ENAME AS Manager,
    M.EMPNO AS "Mgr#"
FROM EMP E
JOIN EMP M
ON E.MGR = M.EMPNO;
```

---

## 5. Outer Join
**Question:**  
Modify the previous query to display all employees including **KING**, who has no manager. Order the results by employee number.

```sql
SELECT
    E.ENAME AS Employee,
    E.EMPNO AS "Emp#",
    M.ENAME AS Manager,
    M.EMPNO AS "Mgr#"
FROM EMP E
LEFT OUTER JOIN EMP M
ON E.MGR = M.EMPNO
ORDER BY E.EMPNO;
```

---

## 6. Non-Equi Join
**Question:**  
First show the structure of the **SALGRADE** table. Then display the **name, job, department name, salary, and grade** for all employees.

```sql
DESC SALGRADE;
```

```sql
SELECT
    E.ENAME,
    E.JOB,
    D.DNAME,
    E.SAL,
    S.GRADE
FROM EMP E
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE S
ON E.SAL BETWEEN S.LOSAL AND S.HISAL;
```

---

## 7. Outer Join
**Question:**  
Display the **ENAME** and **DNAME** of all employees. Also display department names that do not have any employees working.

```sql
SELECT E.ENAME, D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## 8. Self Join with Outer Join
**Question:**  
Find the names and hire dates for all employees who were hired before their managers, along with their managers' names and hire dates.

```sql
SELECT
    E.ENAME AS Employee,
    E.HIREDATE AS Employee_HireDate,
    M.ENAME AS Manager,
    M.HIREDATE AS Manager_HireDate
FROM EMP E
LEFT OUTER JOIN EMP M
ON E.MGR = M.EMPNO
WHERE M.HIREDATE > E.HIREDATE;
```

---

## 9. USING Clause
**Question:**  
Display the **EMPNO, ENAME, DNAME, LOC** of employees who are working as **CLERK**. Use the **USING** clause.

```sql
SELECT EMPNO, ENAME, DNAME, LOC
FROM EMP
JOIN DEPT
USING (DEPTNO)
WHERE JOB = 'CLERK';
```

---

## 10. ON Clause
**Question:**  
Display the **ENAME, SAL, MGR, DNAME** of employees whose salary is more than **2000**. Use the **ON** clause.

```sql
SELECT E.ENAME, E.SAL, E.MGR, D.DNAME
FROM EMP E
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO
WHERE E.SAL > 2000;
```

---

## 11. LEFT OUTER JOIN
**Question:**  
Display the **EMPNO, ENAME, JOB, DEPTNO, DNAME, LOC** of employees. Use **LEFT OUTER JOIN**.

```sql
SELECT
    E.EMPNO,
    E.ENAME,
    E.JOB,
    E.DEPTNO,
    D.DNAME,
    D.LOC
FROM EMP E
LEFT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## 12. RIGHT OUTER JOIN
**Question:**  
Display the **ENAME** and **DNAME** of employees. Use **RIGHT OUTER JOIN**.

```sql
SELECT E.ENAME, D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## 13. FULL OUTER JOIN
**Question:**  
Display the **EMPNO, DNAME, LOC** of employees. Use **FULL OUTER JOIN**.

```sql
SELECT
    E.EMPNO,
    D.DNAME,
    D.LOC
FROM EMP E
FULL OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```
