# Objective: To familiarize with the SQL statements (DML, DDL).

SQL (Structured Query Language) defines the structure of the data, modify data in the database, and specify security constraints apart from just querying database. It is also the standard relational database language. SQL (Structured Query Language) is a database computer language designed for the retrieval and management of data in relational database management systems (RDBMS), database schema creation and modification, and database object access control rhanagement.

It can be categorized broadly into two major categories:

    1. DDL (Data Definition Language): Provides certain commands to specify the certain
    set of definitions by a special language. Also used to specify additional properties of the
    data. E.g. Create, Alter, Drop, Grant, and Revoke.

    2. DML (Data Manipulation language): Data Manipulation commands are the most frequently used SQL
    commands and they are as follow, DML commands are Insert. Select, Update,Delete. DML provides certain
    commands that enable users to access or manipulate data from the schema or relation.e.g. Select Insert, Update and Delete.
    
Consider the schema for the relation employee is given as:

Employee (empno, ename, designation, hiredate, salary, comm, deptno)

The SQL query to create a table employee is as :

```sql
    -- Create Table
    CREATE TABLE EMPLOYEE
        (
            EMPNO           NUMBER(4),
            ENAME           VARCHAR2(20),
            DESIGNATION     VARCHAR2(25),
            HIREDATE        DATE,
            SALARY          NUMBER(10),
            COMM            NUMBER(10,2),
            DEPTNO          NUMBER(4)
        );

    -- Insert Values
    INSERT INTO EMPLOYEE VALUES(1011,'Ram','Manager','01-jan-95',20000,800,100);
    INSERT INTO EMPLOYEE VALUES(1021,'Hari','Accountant','04-apr-99',15000,650,200);
    INSERT INTO EMPLOYEE VALUES(1456,'Shyam','Clerk','03-jul-95',12000,500,300);
    INSERT INTO EMPLOYEE VALUES(1045,'Sita','Analyst','06-oct-98',18000,700,400);
    INSERT INTO EMPLOYEE VALUES(1099,'Ramesh','Clerk','01-jan-96',10000,400,300);
    INSERT INTO EMPLOYEE VALUES(1060,'Hari','Clerk','25-dec-97',10000,400,300);

```

## Write SQL statements for the following queries:

1. Find all the information about the employee.

```sql
SELECT * FROM EMPLOYEE;

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                  Manager                   01-JAN-95      20000        800        100
      1021 Hari                 Accountant                04-APR-99      15000        650        200
      1456 Shyam                Clerk                     03-JUL-95      12000        500        300
      1045 Sita                 Analyst                   06-OCT-98      18000        700        400
      1099 Ramesh               Clerk                     01-JAN-96      10000        400        300
      1060 Hari                 Clerk                     25-DEC-97      10000        400        300
```

2. Find name, designation and salary of all the employee.

```sql
-- Query
SELECT ENAME,DESIGNATION,SALARY FROM EMPLOYEE;

-- Result
    ENAME                DESIGNATION                   SALARY
-------------------- ------------------------- ----------
Ram                  Manager                        20000
Hari                 Accountant                     15000
Shyam                Clerk                          12000
Sita                 Analyst                        18000
Ramesh               Clerk                          10000
Hari                 Clerk                          10000
```

3. Find the names of all employees who work as a clerk.

```sql
-- Query
SELECT ENAME FROM EMPLOYEE WHERE DESIGNATION='Clerk';

--Result
ENAME
--------------------
Shyam
Ramesh
Hari
```

4. Find the information of all clerks working in department number 300.

```sql
--Query
    SELECT * FROM EMPLOYEE WHERE DEPTNO=300;

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1456 Shyam                Clerk                     03-JUL-95      12000        500        300
      1099 Ramesh               Clerk                     01-JAN-96      10000        400        300
      1060 Hari                 Clerk                     25-DEC-97      10000        400        300
```

5. Find name, employee number and designation of the employee who works as manager or analyst.

```sql
-- Query
SELECT ENAME,EMPNO,DESIGNATION FROM EMPLOYEE WHERE DESIGNATION='Manager' OR DESIGNATION='Analyst';
-- or
SELECT * FROM EMPLOYEE WHERE DESIGNATION IN ('Manager','Analyst');

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                  Manager                   01-JAN-95      20000        800        100
      1045 Sita                 Analyst                   06-OCT-98      18000        700        400
```

6. Find the records of all the employees except those whose designation is either Manager or Clerk.

```sql
-- Query
    SELECT * FROM EMPLOYEE WHERE DESIGNATION NOT IN ('Manager','Clerk');

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1021 Hari                 Accountant                04-APR-99      15000        650        200
      1045 Sita                 Analyst                   06-OCT-98      18000        700        400
```

7.  Find the records of all the employees whose designation is either Clerk or Analyst.

```sql
-- Query
     SELECT * FROM EMPLOYEE WHERE DESIGNATION IN ('Clerk','Analyst');

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1456 Shyam                Clerk                     03-JUL-95      12000        500        300
      1045 Sita                 Analyst                   06-OCT-98      18000        700        400
      1099 Ramesh               Clerk                     01-JAN-96      10000        400        300
      1060 Hari                 Clerk                     25-DEC-97      10000        400        300
```

8. Find employee name, salary of all the employee whose salary is equal to 12000 and less than or equal to 20000.

```sql
-- Query
     SELECT ENAME,SALARY FROM EMPLOYEE WHERE (SALARY>=12000 AND SALARY<=20000);

-- Result
ENAME                    SALARY
-------------------- ----------
Ram                       20000
Hari                      15000
Shyam                     12000
Sita                      18000
```

9. Find employee name, salary who earns less than 10000 or more than 15000.

```sql
-- Query
     SELECT ENAME,SALARY FROM EMPLOYEE WHERE (SALARY<10000 OR SALARY>15000);

-- Result
ENAME                    SALARY
-------------------- ----------
Ram                       20000
Sita                      18000
```

10. Find the distinct designation of the employees.

```sql
-- Query
SELECT DISTINCT DESIGNATION FROM EMPLOYEE;

-- Result
DESIGNATION
-------------------------
Manager
Clerk
Analyst
Accountant
```

11. Find the names of employees whose name starts with the alphabet 'R'.

```sql
-- Query
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'R%';

-- Result
ENAME
--------------------
Ram
Ramesh
```

12. Find the employee number and names whose names end in 'm'.

```sql
-- Query
SELECT EMPNO,ENAME FROM EMPLOYEE WHERE ENAME LIKE '%m';

-- Result
     EMPNO ENAME
---------- --------------------
      1011 Ram
      1456 Shyam
```

13. Find the employee name whose name starts with 'H' and ends in i.

```sql
-- Query
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'H%i';

-- Result
ENAME
--------------------
Hari
Hari
```

14. Find the employee name and number whose name starts with 'R' and has two more characters after R.

```sql
-- Query
SELECT ENAME,EMPNO FROM EMPLOYEE WHERE ENAME LIKE 'R__%';

-- Result
ENAME                     EMPNO
-------------------- ----------
Ram                        1011
Ramesh                     1099
```

15. Find the names of the employees in ascending, descending order;

```sql
-- Query
    -- Ascending
SELECT ENAME FROM EMPLOYEE ORDER BY ENAME;
    -- Descending
SELECT ENAME FROM EMPLOYEE ORDER BY ENAME DESC;

-- Result
    -- Ascending                        -- Descending
        ENAME                               ENAME
    --------------------                --------------------
    Hari                                Sita
    Hari                                Shyam
    Ram                                 Ramesh
    Ramesh                              Ram
    Shyam                               Hari
    Sita                                Hari
```

16. Display the names and salaries of all the employees after increasing the salary by 20%.

```sql
-- Query
SELECT ENAME,(SALARY+SALARY*0.2) AS SALARY FROM EMPLOYEE;

-- Result
ENAME                    SALARY
-------------------- ----------
Ram                       24000
Hari                      18000
Shyam                     14400
Sita                      21600
Ramesh                    12000
Hari                      12000
```

17. Display the names and commission of all the employees after incrementing the commission by 20%.

```sql
-- Query
SELECT ENAME,(COMM+COMM*0.2) AS COMM FROM EMPLOYEE;

-- Result
ENAME                      COMM
-------------------- ----------
Ram                         960
Hari                        780
Shyam                       600
Sita                        840
Ramesh                      480
Hari                        480
```

18. Display the name and total salary (Salary + Commission) of all the employees

```sql
-- Query
SELECT ENAME,(SALARY+COMM) AS "TOTAL SALARY" FROM EMPLOYEE;

-- Result
ENAME                TOTAL SALARY
-------------------- ------------
Ram                         20800
Hari                        15650
Shyam                       12500
Sita                        18700
Ramesh                      10400
Hari                        10400
```

19. Find the records of all the employees who work as manager or earns more than 12000.

```sql
-- Query
SELECT * FROM EMPLOYEE WHERE DESIGNATION='Manager' OR SALARY>12000;

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                  Manager                   01-JAN-95      20000        800        100
      1021 Hari                 Accountant                04-APR-99      15000        650        200
      1045 Sita                 Analyst                   06-OCT-98      18000        700        400
```

20. Find the total salary paid to all the employees.

```sql
-- Query
SELECT SUM(SALARY) AS "TOTAL SALARY" FROM EMPLOYEE;

-- Result
TOTAL SALARY
------------
       85000
```

21. Find the total number of record of all the employees.

```sql
-- Query
SELECT COUNT(*) AS "TOTAL RECORDS" FROM EMPLOYEE;

-- Result
TOTAL RECORDS
-------------
            6
```

22. Find the total number of departments.

```sql
-- Query
SELECT COUNT(DISTINCT DEPTNO) AS "TOTAL DEPARTMENTS" FROM EMPLOYEE;

-- Result
TOTAL DEPARTMENTS
-----------------
                4
```

23)Find the maximum salary of each department.

```sql
-- Query
SELECT MAX(SALARY) AS "MAX SALARY",DEPTNO FROM EMPLOYEE GROUP BY DEPTNO;

-- Result
MAX SALARY     DEPTNO
---------- ----------
     20000        100
     18000        400
     12000        300
     15000        200
```

24. Find all the records of employee who has highest salary.

```sql
-- Query
SELECT * FROM EMPLOYEE WHERE SALARY=(SELECT MAX(SALARY) FROM EMPLOYEE);

-- Result
     EMPNO ENAME                DESIGNATION               HIREDATE      SALARY       COMM     DEPTNO
---------- -------------------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                  Manager                   01-JAN-95      20000        800        100
```

25. Find the department number of the employee who gets salary more than the average salary.

```sql
-- Query
SELECT DEPTNO FROM EMPLOYEE WHERE SALARY>(SELECT AVG(SALARY) FROM EMPLOYEE);

-- Result
    DEPTNO
----------
       100
       200
       400
```

26. Find the department number that pays salary more than 12000

```sql
-- Query
SELECT DEPTNO FROM EMPLOYEE WHERE SALARY>12000;

-- Result
    DEPTNO
----------
       100
       200
       400
```
