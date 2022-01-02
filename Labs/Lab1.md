# Objective: To familiarize with the SQL statements (DML, DDL).

SQL (Structured Query Language) defines the structure of the data, modify data in the database, and specify security constraints apart from just querying database. It is also the standard relational database language. SQL (Structured Query Language) is a database computer language designed for the retrieval and management of data in relational database management systems (RDBMS), database schema creation and modification, and database object access control rhanagement.

It can be categorized broadly into two major categories: 1. DDL (Data Definition Language): Provides certain commands to specify the certain
set of definitions by a special language. Also used to specify additional properties of the
data. E.g. Create, Alter, Drop, Grant, and Revoke.

    2. DML (Data Manipulation language): Data Manipulation commands are the most frequently used SQL commands and they are as follow, DML commands are Insert. Select, Update, Delete. DML provides certain commands that enable users to access or manipulate data from the schema or relation.e.g. Select Insert, Update and Delete.

The Select Command: The select command has four basic parts:
i) The word select followed by the list of attributes desired in the result.
ii) The word from followed by the relation/schema from where the data is retrieved.
iii) The word where followed by the selection criterion.
iv) The word order/group by followed by criterion.

Consider the schema for the relation employee is given as:
Employee (empno, ename, designation, hiredate, salary, comm, deptno)
The SQL query to create a table employee is as :

```sql
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
```

```sql

```