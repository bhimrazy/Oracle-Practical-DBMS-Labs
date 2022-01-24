# LAB 3 : To familiarize with the SQL statements and the constraints.

## Objective:

    i) To familiarize with the SQL DML statements like Create, Alter, Drop.
    ii) To familiarize with the constraints (Primary Constraints and Check Constraints)

### Sample relations:

    1.Student schema (crn, name, address, phone, dob)
    2.Department schema (deptid, dnumber, dname)
    3.Course schema (Courseid, coursename, duration, fee)

### Write SQL Statements for the following:

1. Create a relation student on the student schema with the underlined attribute as a primary key. The attribute is not null.

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
    ----------------------------------------- -------- ----------------
    CRN                                       NOT NULL VARCHAR2(12)
    NAME                                      NOT NULL VARCHAR2(20)
    ADDRESS                                   NOT NULL VARCHAR2(25)
    PHONE                                     NOT NULL NUMBER(10)
    DOB                                                DATE
```

2. Insert a tuple into relation student with crn as null. Comment.

```sql
    -- Query
    INSERT INTO STUDENT VALUES(null,'Ram','Kathmandu',9800452486,'01-jan-95');

    -- Comment : cannot insert null
    -- This is because we have specified CRN as primary key which by default
    -- donot accept null value
```

3. Insert a tuple into student with crn 066/bct/045. Comment.

```sql
    -- Query
    INSERT INTO STUDENT VALUES('066/bct/045','Ram','Kathmandu',9800452486,'01-jan-95');

    -- Comment : 1 row created.
    -- The values provided for the insertion satifies the schema and constraints of the table.

    -- Result
        CRN          NAME                 ADDRESS                        PHONE DOB
    ------------ -------------------- ------------------------- ---------- ---------
    066/bct/045  Ram                  Kathmandu                 9800452486 01-JAN-95

```

4. Insert a tuple into student with crn 066/bct/045. Comment.

```sql
    -- Query
    INSERT INTO STUDENT VALUES('066/bct/045','Ram','Kathmandu',9800452486,'01-jan-95');

    -- Comment : ORA-00001: unique constraint violated
    -- Since, CRN is specified as a primary key so by default it only takes unique values.
```

5. Alter the relation student to add parents name and emailid.

```sql
    -- Query
    ALTER TABLE STUDENT ADD (parentsname varchar2(25), emailid varchar2(30));

    -- Result
        Name                                     Null?     Type
    ----------------------------------------    --------- -----------
        CRN                                      NOT NULL  VARCHAR2(12)
        NAME                                     NOT NULL  VARCHAR2(20)
        ADDRESS                                  NOT NULL  VARCHAR2(25)
        PHONE                                    NOT NULL  NUMBER(10)
        DOB                                                DATE
        PARENTSNAME                                        VARCHAR2(25)
        EMAILID                                            VARCHAR2(30)
```

6. Create a relation department on the department schema with the underlined attribute as primary key.
Add the constraint to the relation department such that dnumber is only between 10 and 50 and also dname should be in capital letter.

```sql
    -- Query
    CREATE TABLE DEPARTMENT
        (
            DEPTID           VARCHAR2(5) PRIMARY KEY,
            DNUMBER          VARCHAR2(3) NOT NULL,
            DNAME            VARCHAR2(20) NOT NULL
        );

    -- Adds constraint to check dnumber lies in only between 10 and 50.
    ALTER TABLE DEPARTMENT ADD CONSTRAINT DNUM_CHK CHECK (DNUMBER >=10 and DNUMBER <=50);
    -- Adds constraint to check dname is always capital.
    ALTER TABLE DEPARTMENT ADD CONSTRAINT DNAME_CHK CHECK (DNAME = UPPER(DNAME));


```

7. Insert a tuple into a relation department with dnumber as 10 and dname as COMPUTER. Comment.

```sql
    -- Query
    INSERT INTO DEPARTMENT VALUES('IT01','10','COMPUTER'); --1 row created.

    -- Result
    DEPTID  DNUMBER   DNAME
    -----   --------  ----------
    IT01    10        COMPUTER
```

8. Insert a tuple into a relation department with dnumber as 20 and dname as Civil. Comment.

```sql
    -- Query
    INSERT INTO DEPARTMENT VALUES('CE01','20','Civil');

    -- Comment : ORA-02290: check constraint (DNAME_CHK) violated
    -- Since, a constraint for DNAME i.e DNAME_CHK is added which checks if all the DNAME field
    -- are capital.

```

9. Create a relation course on course schema with the underlined attribute as primary key. The course name is unique.

```sql
    -- Query
    CREATE TABLE COURSE
         (
            COURSEID           VARCHAR2(5) PRIMARY KEY,
            COURSENAME         VARCHAR2(20) NOT NULL,
            DURATION           NUMBER(10) NOT NULL,
            FEE                NUMBER(10) NOT NULL
        );

     -- Adds constraint to check all coursenames are unique.
    ALTER TABLE COURSE ADD CONSTRAINT CNAME_UNQ UNIQUE(COURSENAME); -- Table altered.

```

10. Add a constraint to the relation course such that the minimum fee for all courses is 5000.

```sql
    -- Query
    -- Adds constraint to check minimum fee for all courses is 5000.
    ALTER TABLE COURSE ADD CONSTRAINT FEE_CHK CHECK(FEE>=5000); -- Table altered.
```

11. Fill in the table course with the data of your choices provided that the courses offered are only LINUX, ORACLE, JAVA and CISCO.

```sql
    -- Query
    ALTER TABLE COURSE ADD CONSTRAINT CNAME_CHK CHECK(COURSENAME IN ('JAVA','LINUX','ORACLE','CISCO')); -- Table altered.
```

12. Insert a tuple into the relation course with the course name Visual Basic. Comment.

```sql
    -- Query
    INSERT INTO COURSE VALUES('VS01','Visual Basic',2,8000);

    -- Comment : check constraint (CNAME_CHK) violated
    -- Since, a constraint for COURSENAME i.e CNAME_CHK is added which checks if all the COURSENAME field
    -- lies with in ('JAVA','LINUX','ORACLE','CISCO') these fields.

```

13. Add a constraint to the relation student so that the attributes phone number and dob together form a unique key.

```sql
    -- Query
    -- Adds constraint
    ALTER TABLE STUDENT ADD CONSTRAINT STU_UNQ UNIQUE(PHONE,DOB); -- Table altered.
```

14. Insert a tuple into relation student with dob as null. Comment.

```sql
    -- Query
    INSERT INTO STUDENT STUDENT VALUES('075/bct/045','Hari','Kathmandu',9800452486,null,'Mohan','eamil@email.com');

    -- Comment : -- 1 row created.
    -- Since, DOB field also accepts null field , the data get's inserted.

```

15. Insert a tuple into the relation student with the attributes phone number as null value. Comment.

```sql
    -- Query
    INSERT INTO STUDENT STUDENT VALUES('077/bct/045','Ramesh','Kathmandu',null,'05-jan-95','Jetu','eamil@email.com');

    -- Comment : ORA-01400: cannot insert NULL into ("STUDENT"."PHONE")
    -- Since, there is NOT NULL constraint in schema of student , so it doesnot allow data insertion with null phone no.

```

16. Insert a tuple into the relation student with both the attribute phone number and dob as null value. Comment.

```sql
    -- Query
    INSERT INTO STUDENT STUDENT VALUES('077/bct/045','Ramesh','Kathmandu',null,null,'Jetu','eamil@email.com');

    -- Comment : ORA-01400: cannot insert NULL into ("STUDENT"."PHONE")
    -- Since, there is NOT NULL constraint in schema of student , so it doesnot allow data insertion with null phone no.

```

17. Drop the constraint applied to dname of schema department.

```sql
    -- Query
    ALTER TABLE DEPARTMENT DROP CONSTRAINT DNAME_CHK; -- Table altered.
```

18. Alter the relation Course to change the data type from integer to floating point.

```sql
    -- Query
    ALTER TABLE COURSE MODIFY FEE NUMBER(10,2); -- Table altered.
```

19. Drop the constraint applied on combination of attributes phone number and dob from relation student.

```sql
    -- Query
    ALTER TABLE STUDENT DROP CONSTRAINT STU_UNQ;  -- Table altered.
```

20. Delete all the records from the relation student.

```sql
    -- Query
    DELETE STUDENT;  -- All rows deleted.
```

21. Remove the relation student from the database.

```sql
    -- Query
    DROP TABLE STUDENT;  -- Table dropped.
```

22. Remove the relation course and department from the database.

```sql
    -- Query
    DROP TABLE COURSE;  -- Table dropped.
    DROP TABLE DEPARTMENT; -- Table dropped.
```
