# LAB 2 - Objective: To familiarize with the SQL Statements (DML: Insert, Update, Delete) and additional functions.

Data Manipulation Language (Contd...)

1. The Insert command:

To insert data into table, one tuple at a time, the insert command is used in the ways.

i) To insert data into a table(t) of n attributes

-insert into t values ('a1', 'a2'...'an'). ii) To insert data into the specified columns (A1, A2, A3... An). -insert into t (A1, A2, A3....An) values ('a1','a2', 'a3'......'an").

2. The Update command: To modify or update the

command has three parts:

data stored within the table, use update command. The

i) The word update followed by the table you want to change, (mandatory)

ii) The word set followed by one or more columns you want to change (mandatory)

iii) The word where followed by selection criterion (Optional)

General format of command: Update t set A=new value where X.

3. The Delete command: To remove one or more rows of data from a table use delete command. The command

has two parts:

The word delete from followed by the table name you want to remove data ii) The word where followed by the criterion for deletion.

General format of command: Delete from t where X.

The relation of the employees has following description as follows:

empno number not null ename varchar2 not null
Phone number designation varchar2 not null
hiredate date sal number not null
comm number deptno number not null

Write SQL statements for the following queries:

1. Insert the data of the employees given below in the employee schema
   The SQL query to create a table employee and insert values is as :

```sql
    -- Create Table
    CREATE TABLE EMPLOYEE
        (
            EMPNO           NUMBER(4) NOT NULL,
            ENAME           VARCHAR2(20) NOT NULL,
            PHONE           NUMBER(10),
            DESIGNATION     VARCHAR2(25) NOT NULL,
            HIREDATE        DATE,
            SAL             NUMBER(10) NOT NULL,
            COMM            NUMBER(10,2),
            DEPTNO          NUMBER(4) NOT NULL
        );

    -- Insert Values
    INSERT INTO EMPLOYEE VALUES(1011,'Ram','4212222','Manager','01-jan-95',20000,800,100);
    INSERT INTO EMPLOYEE VALUES(1021,'Hari','5432344','Accountant','04-apr-99',15000,650,200);
    INSERT INTO EMPLOYEE VALUES(1456,'Shyam','4235546','Clerk','03-jul-95',12000,500,300);
    INSERT INTO EMPLOYEE(EMPNO,ENAME,DESIGNATION,HIREDATE,SAL,COMM,DEPTNO) VALUES(1045,'Sita','Analyst','06-oct-98',18000,700,400);
    INSERT INTO EMPLOYEE VALUES(1099,'Ramesh','4212222','Clerk','01-jan-96',10000,400,300);
    INSERT INTO EMPLOYEE VALUES(1066,'Hari','4212222','Clerk','25-dec-97',10000,400,300);
    INSERT INTO EMPLOYEE VALUES(1788,'Ramesh','4445534','Sub-Clerk','14-apr-96',8000,300,600);

    -- Result
         EMPNO ENAME                     PHONE DESIGNATION               HIREDATE         SAL       COMM     DEPTNO
---------- -------------------- ---------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                     4212222 Manager                   01-JAN-95      20000        800        100
      1021 Hari                    5432344 Accountant                04-APR-99      15000        650        200
      1456 Shyam                   4235546 Clerk                     03-JUL-95      12000        500        300
      1045 Sita                            Analyst                   06-OCT-98      18000        700        400
      1099 Ramesh                  4212222 Clerk                     01-JAN-96      10000        400        300
      1066 Hari                    4212222 Clerk                     25-DEC-97      10000        400        300
      1788 Ramesh                  4445534 Sub-Clerk                 14-APR-96       8000        300        600
```

2. Increment the salary of all the employees by 20%.
```sql
    -- Query
    UPDATE EMPLOYEE SET SAl=SAL+0.2*SAL;

    -- Result
     EMPNO ENAME                     PHONE DESIGNATION               HIREDATE         SAL       COMM     DEPTNO
---------- -------------------- ---------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                     4212222 Manager                   01-JAN-95      24000        800        100
      1021 Hari                    5432344 Accountant                04-APR-99      18000        650        200
      1456 Shyam                   4235546 Clerk                     03-JUL-95      14400        500        300
      1045 Sita                            Analyst                   06-OCT-98      21600        700        400
      1099 Ramesh                  4212222 Clerk                     01-JAN-96      12000        400        300
      1066 Hari                    4212222 Clerk                     25-DEC-97      12000        400        300
      1788 Ramesh                  4445534 Sub-Clerk                 14-APR-96       9600        300        600
```
3) Update Sita's information to add her telephone number to 4325555.

```sql
    -- Query
    UPDATE EMPLOYEE SET PHONE=4325555 WHERE ENAME='Sita';

    -- Result
     EMPNO ENAME                     PHONE DESIGNATION               HIREDATE         SAL       COMM     DEPTNO
---------- -------------------- ---------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                     4212222 Manager                   01-JAN-95      24000        800        100
      1021 Hari                    5432344 Accountant                04-APR-99      18000        650        200
      1456 Shyam                   4235546 Clerk                     03-JUL-95      14400        500        300
      1045 Sita                    4325555 Analyst                   06-OCT-98      21600        700        400
      1099 Ramesh                  4212222 Clerk                     01-JAN-96      12000        400        300
      1066 Hari                    4212222 Clerk                     25-DEC-97      12000        400        300
      1788 Ramesh                  4445534 Sub-Clerk                 14-APR-96       9600        300        600
```

4. Give all the employee hired before 1997, commission of 10% of salary.
```sql
    -- Query
    UPDATE EMPLOYEE SET COMM=COMM+0.1*COMM WHERE ='Sita';

    -- Result
     EMPNO ENAME                     PHONE DESIGNATION               HIREDATE         SAL       COMM     DEPTNO
---------- -------------------- ---------- ------------------------- --------- ---------- ---------- ----------
      1011 Ram                     4212222 Manager                   01-JAN-95      24000        800        100
      1021 Hari                    5432344 Accountant                04-APR-99      18000        650        200
      1456 Shyam                   4235546 Clerk                     03-JUL-95      14400        500        300
      1045 Sita                    4325555 Analyst                   06-OCT-98      21600        700        400
      1099 Ramesh                  4212222 Clerk                     01-JAN-96      12000        400        300
      1066 Hari                    4212222 Clerk                     25-DEC-97      12000        400        300
      1788 Ramesh                  4445534 Sub-Clerk                 14-APR-96       9600        300        600
```

5. Decrease 15\% of Income tax from all the employees whose total income exceeds

15000

6. Increment salary of employee by hat 1 20\% whose commission ranges from 400 7) Transfer Hari to department 100. 8) Transfer the Ramesh with empid 1788 to department 500.

7. Delete the record of Sita.

8. Delete the record of Shyam whose empidis 1456.

9. Transfer the Hari to department 100 and increment his salary by 1500.

10. Delete all the record of table employee
