# Objective: To familiarize with the SQL statements (DML, DDL).

SQL (Structured Query Language) defines the structure of the data, modify data in the database, and specify security constraints apart from just querying database. It is also the standard relational database language. SQL (Structured Query Language) is a database computer language designed for the retrieval and management of data in relational database management systems (RDBMS), database schema creation and modification, and database object access control rhanagement.

It can be categorized broadly into two major categories: 

    1. DDL (Data Definition Language): Provides certain commands to specify the certain
    set of definitions by a special language. Also used to specify additional properties of the
    data. E.g. Create, Alter, Drop, Grant, and Revoke.

    2. DML (Data Manipulation language): Data Manipulation commands are the most frequently used SQL
    commands and they are as follow, DML commands are Insert. Select, Update,Delete. DML provides certain
    commands that enable users to access or manipulate data from the schema or relation.e.g. Select Insert, Update and Delete.

The Select Command: The select command has four basic parts:
i) The word select followed by the list of attributes desired in the result.
ii) The word from followed by the relation/schema from where the data is retrieved.
iii) The word where followed by the selection criterion.
iv) The word order/group by followed by criterion.

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
1) Find all the information about the employee.
```sql
SELECT * FROM EMPLOYEE;
```
<img src="https://user-images.githubusercontent.com/46085301/147871453-fc733b08-ab2a-4c05-a284-107fcb728dc5.png" height="250"/>

2) Find name, designation and salary of all the employee.
```sql
SELECT ENAME,DESIGNATION,SALARY FROM EMPLOYEE;
```
<img src="https://user-images.githubusercontent.com/46085301/147871799-abe7d48e-62f4-4ed3-b995-a68c1b91c16e.png" height="200"/>

3) Find the names of all employees who work as a clerk.
```sql
SELECT ENAME FROM EMPLOYEE WHERE DESIGNATION='Clerk';  
```
<img src="https://user-images.githubusercontent.com/46085301/147871735-ac050160-3c13-457b-bd09-70c34b33a913.png" height="200"/>

4) Find the information of all clerks working in department number 300.
```sql
    SELECT * FROM EMPLOYEE WHERE DEPTNO=300;
```
<img src="https://user-images.githubusercontent.com/46085301/147871966-bed1e240-55a0-4c3c-a6cd-87ed9e119175.png" height="200"/>

5) Find name, employee number and designation of the employee who works as manager or analyst.
```sql
SELECT ENAME,EMPNO,DESIGNATION FROM EMPLOYEE WHERE DESIGNATION='Manager' or DESIGNATION='Analyst';    
-- or
SELECT * FROM EMPLOYEE WHERE DESIGNATION IN ('Manager','Analyst');    
```
<img src="https://user-images.githubusercontent.com/46085301/147872226-09cb68cc-af8c-452e-975f-70d61e664933.png" height="200"/>

6) Find the records of all the employees except those whose designation is either Manager or Clerk.
```sql
    SELECT * FROM EMPLOYEE WHERE DESIGNATION NOT IN ('Manager','Clerk');    
```
![image](https://user-images.githubusercontent.com/46085301/147872425-8480b393-1741-417c-b69f-cde28eee4314.png)

<img src="https://user-images.githubusercontent.com/46085301/" height="200"/>
7)  Find the records of all the employees whose designation is either Clerk or Analyst.
```sql
     SELECT * FROM EMPLOYEE WHERE DESIGNATION IN ('Clerk','Analyst');    
```
![image](https://user-images.githubusercontent.com/46085301/147872639-9aead629-91b6-4f4d-95b8-6663b7a02394.png)

8) Find employee name, salary of all the employee whose salary is equal to 12000 and less than or equal to 20000. 
```sql
     SELECT ENAME,SALARY FROM EMPLOYEE WHERE (SALARY>=12000 and SALARY<=20000);    
```
![image](https://user-images.githubusercontent.com/46085301/147872752-32a7ba03-d3a1-407c-81d9-a1fca9c903cb.png)

9) Find employee name, salary who earns less than 10000 or more than 15000.
```sql
     SELECT ENAME,SALARY FROM EMPLOYEE WHERE (SALARY<10000 or SALARY>15000);    
```
10) Find the distinct designation of the employees.
```sql
SELECT DISTINCT DESIGNATION FROM EMPLOYEE;
```
![image](https://user-images.githubusercontent.com/46085301/147872874-a7296ac6-c0b9-4e52-920a-1ab29f1ad3c1.png)

11) Find the names of employees whose name starts with the alphabet 'R'.
```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'R%';
```
![image](https://user-images.githubusercontent.com/46085301/147872938-d84904d6-7120-4001-92e5-4af326b124a2.png)

12) Find the employee number and names whose names end in 'm'. 
```sql
SELECT EMPNO,ENAME FROM EMPLOYEE WHERE ENAME LIKE '%m';
```
![image](https://user-images.githubusercontent.com/46085301/147873023-936daa62-2361-41ff-9727-ab2747c4fae4.png)


13) Find the employee name whose name starts with 'H' and ends in i. 
```sql
SELECT ENAME FROM EMPLOYEE WHERE ENAME LIKE 'H%i';
```
![image](https://user-images.githubusercontent.com/46085301/147873014-c8f9b6a7-f623-4d18-9034-3280a61f40f5.png)

14) Find the employee name and number whose name starts with 'R' and has two more characters after R.
```sql
SELECT ENAME,EMPNO FROM EMPLOYEE WHERE ENAME LIKE 'R__%';
```
![image](https://user-images.githubusercontent.com/46085301/147873083-4af9db9e-844e-447e-8dc4-fa38538a9ff0.png)

15) Find the names of the employees in ascending, descending order;
```sql
-- Ascending
SELECT ENAME FROM EMPLOYEE ORDER BY ENAME;
-- Descending
SELECT ENAME FROM EMPLOYEE ORDER BY ENAME DESC;
```
![image](https://user-images.githubusercontent.com/46085301/147873224-fa341edf-b207-4a10-b6f6-433d63f85ac5.png)
![image](https://user-images.githubusercontent.com/46085301/147873239-27a28766-8db2-4af1-b65f-70fb2796e417.png)

16) Display the names and salaries of all the employees after increasing the salary by 20%. 
```sql
SELECT ENAME,(SALARY+SALARY*0.2) AS SALARY FROM EMPLOYEE;
```
17) Display the names and commission of all the employees after incrementing the commission by 20%.
```sql
SELECT ENAME,(COMM+COMM*0.2) AS COMM FROM EMPLOYEE;
```
18) Display the name and total salary (Salary + Commission) of all the employees 19) Find the records of all the employees who work as manager or earns more than 12000.

20) Find the total salary paid to all the employees

21) Find the total number of record of all the employees

22) Find the total number of departments. 23)Find the maximum salary of each department.

24) Find all the records of employee who has highest salary.

1014

25) Find the department number of the employee who gets salary more than the average

salary.

26) Find the department number that pays salary more than 12000
