# LAB 3 : To familiarize with the SQL statements and the constraints.

## Objective: 

i) To familiarize with the SQL DML statements like Create, Alter, Drop.
ii) To familiarize with the constraints (Primary Constraints and Check Constraints)

### Sample relations:

1.Student schema (crn, name, address, phone, dob)
2.Department schema (deptid, dnumber, dname)
3.Course schema (Courseid, coursename, duration, fee)

### Write SQL Statements for the following:
1.Create a relation student on the student schema with the underlined attribute as a primary key. The attribute is not null.

```sql

    -- Query
    CREATE TABLE STUDENT
        (
            CRN           VARCHAR2(12) PRIMARY KEY,
            NAME          VARCHAR2(20) NOT NULL,
            ADDRESS       VARCHAR2(25) NOT NULL,
            PHONE         NUMBER(10)   NOT NULL,
            DOB           DATE
        );

    -- Result

    Name                                      Null?    Type
    ----------------------------------------- -------- ----------------------------
    CRN                                       NOT NULL VARCHAR2(12)
    NAME                                      NOT NULL VARCHAR2(20)
    ADDRESS                                   NOT NULL VARCHAR2(25)
    PHONE                                     NOT NULL NUMBER(10)
    DOB                                                DATE


```

2.Insert a tuple into relation student with crn as null. Comment.

```sql
     INSERT INTO STUDENT VALUES(null,'Ram','Kathmandu',9800452486,'01-jan-95'); -- cannot insert null
```
3.Insert a tuple into student with crn 066/bct/045. Comment.
```sql
     INSERT INTO STUDENT VALUES('066/bct/045','Ram','Kathmandu',9800452486,'01-jan-95'); --1 row created.

     CRN          NAME                 ADDRESS                        PHONE DOB
------------ -------------------- ------------------------- ---------- ---------
066/bct/045  Ram                  Kathmandu                 9800452486 01-JAN-95

```
4.Insert a tuple into student with crn 066/bct/045. Comment.

```sql
     INSERT INTO STUDENT VALUES('066/bct/045','Ram','Kathmandu',9800452486,'01-jan-95'); --ORA-00001: unique constraint (BHIM.SYS_C0011634) violated
```
5.Alter the relation student to add parents name and emailid.
```sql

    ALTER TABLE STUDENT ADD (parentsname varchar2(25), emailid varchar2(30));

    -- Result
        Name                                                                                                              Null?    Type
    ----------------------------------------------------------------------------------------------------------------- -------- -
    CRN                                                                                                               NOT NULL VARCHAR2(12)
    NAME                                                                                                              NOT NULL VARCHAR2(20)
    ADDRESS                                                                                                           NOT NULL VARCHAR2(25)
    PHONE                                                                                                             NOT NULL NUMBER(10)
    DOB                                                                                                                        DATE
    PARENTSNAME                                                                                                                VARCHAR2(25)

```
6.Create a relation department on the department schema with the underlined attribute as primary key. Add the constraint to the relation department such that dnumber is only between 10 and 50 and also dname should be in capital letter.
```sql
    -- Query
    -- 
        CREATE TABLE DEPARTMENT
        (
            DEPTID           VARCHAR2(5) PRIMARY KEY,
            DNUMBER          VARCHAR2(3) NOT NULL,
            DNAME            VARCHAR2(20) NOT NULL
        );

    -- Add constraint
    ALTER TABLE DEPARTMENT ADD CONSTRAINT DNUM_CHK CHECK (DNUMBER >=10 and DNUMBER <=50);

    ALTER TABLE DEPARTMENT ADD CONSTRAINT DNAME_CHK CHECK (DNAME = UPPER(DNAME));
    -- Result

```

7.Insert a tuple into a relation department with dnumber as 10 and dname as COMPUTER. Comment.
```sql

     INSERT INTO DEPARTMENT VALUES('IT01','10','COMPUTER'); --1 row created.

```
8.Insert a tuple into a relation department with dnumber as 20 and dname as Civil. Comment.

```sql

    INSERT INTO DEPARTMENT VALUES('CE01','20','Civil'); -- ORA-02290: check constraint (BHIM.DNAME_CHK) violated

    INSERT INTO DEPARTMENT VALUES('CE01','60','CIVIL'); -- ORA-02290: check constraint (BHIM.DNUM_CHK) violated

    INSERT INTO DEPARTMENT VALUES('CE01','20','CIVIL'); -- 1 row created.
```
9.Create a relation course on course schema with the underlined attribute as primary key. The course name is unique.
```sql
    -- Query
    -- 
    CREATE TABLE COURSE
         (
            COURSEID           VARCHAR2(5) PRIMARY KEY,
            COURSENAME         VARCHAR2(20) NOT NULL,
            DURATION           NUMBER(10) NOT NULL,
            FEE                NUMBER(10) NOT NULL
        );

    -- Add constraint
    ALTER TABLE COURSE ADD CONSTRAINT CNAME_UNQ UNIQUE(COURSENAME); -- Table altered.

    -- Result

```

10.Add a constraint to the relation course such that the minimum fee for all courses is 5000.
```sql
    -- Add constraint
    ALTER TABLE COURSE ADD CONSTRAINT FEE_CHK CHECK(FEE>=5000); -- Table altered.
```
11.Fill in the table course with the data of your choices provided that the courses offered are only LINUX, ORACLE, JAVA and CISCO.
```sql

    ALTER TABLE COURSE ADD CONSTRAINT CNAME_CHK CHECK(COURSENAME IN ('JAVA','LINUX','ORACLE','CISCO')); -- Table altered.
```
12.Insert a tuple into the relation course with the course name Visual Basic. Comment.
```sql

     INSERT INTO COURSE VALUES('VS01','Visual Basic',2,8000); --check constraint (BHIM.CNAME_CHK) violated
     
     INSERT INTO COURSE VALUES('DN01','JAVA',2,8000); -- 1 row created.

```
13.Add a constraint to the relation student so that the attributes phone number and dob together form a unique key.
```sql
    -- Add constraint
    ALTER TABLE STUDENT ADD CONSTRAINT STU_UNQ UNIQUE(PHONE,DOB); -- Table altered.
```
14.Insert a tuple into relation student with dob as null. Comment.
```sql
    INSERT INTO STUDENT STUDENT VALUES('075/bct/045','Hari','Kathmandu',9800452486,null,'Mohan','eamil@email.com'); -- 1 row created.

```
15.Insert a tuple into the relation student with the attributes phone number as null value. Comment.
```sql
    INSERT INTO STUDENT STUDENT VALUES('077/bct/045','Ramesh','Kathmandu',null,null,'Jetu','eamil@email.com'); -- ORA-01400: cannot insert NULL into ("BHIM"."STUDENT"."PHONE")

```
16.Insert a tuple into the relation student with both the attribute phone number and dob as null value. Comment.
```sql
    INSERT INTO STUDENT STUDENT VALUES('077/bct/045','Ramesh','Kathmandu',null,null,'Jetu','eamil@email.com'); -- ORA-01400: cannot insert NULL into ("BHIM"."STUDENT"."PHONE")

```
17.Drop the constraint applied to dname of schema department.
```sql
    ALTER TABLE DEPARTMENT DROP CONSTRAINT DNAME_CHK;
```
18.Alter the relation Course to change the data type from integer to floating point.
```sql
    ALTER TABLE COURSE MODIFY FEE NUMBER(10,2); -- Table altered.
```
19.Drop the constraint applied on combination of attributes phone number and dob from relation student.
```sql
    ALTER TABLE STUDENT DROP CONSTRAINT STU_UNQ;  -- Table altered.
```
20.Delete all the records from the relation student.
```sql
    DELETE STUDENT;  -- 2 rows deleted.
```
21.Remove the relation student from the database.
```sql
    DROP TABLE STUDENT;  -- Table dropped.
```
22.Remove the relation course and department from the database.
```sql
    DROP TABLE COURSE;  -- Table dropped.
    DROP TABLE DEPARTMENT; -- Table dropped.
```