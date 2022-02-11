# LAB 4 : To familiarize with the referential integrity and the views.

## Objective:

    i) To familiarize with the referential integrity in SQL (Foreign Key).
    ii) To familiarize with the views.

### Sample relations:

    1.Student schema (crn, name, address, phone, DOB)
    2.Course schema (courseid, cname, duration, fee)
    3.Enroll schema (enrolled, crn, coursed, enrolldt, completedt)

### Write SQL Statements for the following:

1.Create a table student on student schema with crn as primary key and a table course on course schema with course id as primary key.

```sql

    -- Query
    CREATE TABLE STUDENT
            (
                CRN           VARCHAR2(14) PRIMARY KEY,
                NAME          VARCHAR2(20) NOT NULL,
                ADDRESS       VARCHAR2(25) NOT NULL,
                PHONE         NUMBER(10)   NOT NULL,
                DOB           DATE
            );

    CREATE TABLE COURSE
            (
                COURSEID           VARCHAR2(5) PRIMARY KEY,
                CNAME              VARCHAR2(20) NOT NULL,
                DURATION           NUMBER(10) NOT NULL,
                FEE                NUMBER(10) NOT NULL
            );

    -- Result
    TNAME                                                       TABTYPE
------------------------------------------------------------ -----------------
    COURSE                                                       TABLE
    STUDENT                                                      TABLE


```

2. Insert the following tuples into relation student.

```sql
    -- Query
    INSERT INTO STUDENT VALUES('075/bct/112','Anil','Lalitpur',9845268,'12-jan-1992');
    INSERT INTO STUDENT VALUES('075/bct/115','Bibek','Bhaktapur',98452688,'01-apr-1990');
    INSERT INTO STUDENT VALUES('075/bct/166','Rohan','New Road',984548268,'12-mar-1992');
    INSERT INTO STUDENT VALUES('075/bct/188','Puja','Baneshwor',42322432,'12-jul-1989');
    INSERT INTO STUDENT VALUES('075/bct/154','John','Jorpati',51423234,'18-dec-1993');
    INSERT INTO STUDENT VALUES('075/bct/176','Sita','Lagankhel',51222765,'10-jun-1989');

    -- Result

    CRN            NAME                 ADDRESS                        PHONE DOB
    -------------- -------------------- ------------------------- ---------- ---------
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89


```

3. Insert the following tuples into the relation course:

```sql
    -- Query
    INSERT INTO COURSE VALUES('C101','Java',5,12000);
    INSERT INTO COURSE VALUES('C102','Oracle',8,21000);
    INSERT INTO COURSE VALUES('C103','Linux',3,15000);
    INSERT INTO COURSE VALUES('C104','Cisco',2,22000);

    -- Result
    COURS CNAME                  DURATION        FEE
    ----- -------------------- ---------- ----------
    C101  Java                          5      12000
    C102  Oracle                        8      21000
    C103  Linux                         3      15000
    C104  Cisco                         2      22000

```

4.Create a relation enroll with enroll id as primary key. Attributes crn and course id are
foreign keys referencing relation student and course respectively.

```sql
    -- Query
    CREATE TABLE ENROLL
         (
            ENROLLID           VARCHAR2(4) PRIMARY KEY,
            CRN                VARCHAR2(14) ,
            CID                VARCHAR2(5) ,
            ENROLLDT           DATE,
            COMPLETEDT         DATE,
            FOREIGN KEY(CRN) REFERENCES STUDENT(CRN),
            FOREIGN KEY(CID) REFERENCES COURSE(COURSEID)
        );

```

5.Insert the following tuples into the relation enroll:

```sql
    -- Query
    INSERT INTO ENROLL VALUES('E12','075/bct/112','C101','23-jan-2011',Null);
    INSERT INTO ENROLL VALUES('E13','075/bct/115','C101','23-jan-2011','1-jun-2011');
    INSERT INTO ENROLL VALUES('E14','075/bct/176','C103','01-jun-2012',Null);
    INSERT INTO ENROLL VALUES('E15','075/bct/176','C102','01-jun-2012',Null);
    INSERT INTO ENROLL VALUES('E18','075/bct/115','C104','01-mar-2012',Null);
    INSERT INTO ENROLL VALUES('E20','075/bct/166','C101','01-apr-2012',Null);
    INSERT INTO ENROLL VALUES('E30','075/bct/188','C101','23-apr-2012',Null);

    -- Result
    ENRO CRN            CID   ENROLLDT  COMPLETED
    ---- -------------- ----- --------- ---------
    E12  075/bct/112    C101  23-JAN-11
    E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    E14  075/bct/176    C103  01-JUN-12
    E15  075/bct/176    C102  01-JUN-12
    E18  075/bct/115    C104  01-MAR-12
    E20  075/bct/166    C101  01-APR-12
    E30  075/bct/188    C101  23-APR-12

```

6.Insert a tuple into the relation enroll with enroll id e23, crn 075/bct/112 and course id
C105. Comment.

```sql
    -- Query
    INSERT INTO ENROLL VALUES('E23','075/bct/112','C105','23-jan-2011',Null);
    INSERT INTO ENROLL VALUES('E89','075/bct/119','C101','23-jan-2011',Null);


    -- Comment : ORA-02291: integrity constraint violated - parent key not found
    -- Inserting data with unknown parent key is restricted by validation constraint
```

7.Find the Cartesian product of student and enroll.

```sql
    -- Query
    SELECT * FROM STUDENT,ENROLL ;
    --OR
    SELECT * FROM STUDENT CROSS JOIN ENROLL;

    -- Result
    CRN            NAME                 ADDRESS                        PHONE DOB       ENRO CRN            CID   ENROLLDT  COMPLETED
    -------------- -------------------- ------------------------- ---------- --------- ---- -------------- ----- --------- ---------
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E12  075/bct/112    C101  23-JAN-11
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E14  075/bct/176    C103  01-JUN-12
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E15  075/bct/176    C102  01-JUN-12
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E18  075/bct/115    C104  01-MAR-12
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E20  075/bct/166    C101  01-APR-12
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E30  075/bct/188    C101  23-APR-12
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E12  075/bct/112    C101  23-JAN-11
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E14  075/bct/176    C103  01-JUN-12
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E15  075/bct/176    C102  01-JUN-12

    CRN            NAME                 ADDRESS                        PHONE DOB       ENRO CRN            CID   ENROLLDT  COMPLETED
    -------------- -------------------- ------------------------- ---------- --------- ---- -------------- ----- --------- ---------
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E18  075/bct/115    C104  01-MAR-12
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E20  075/bct/166    C101  01-APR-12
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E30  075/bct/188    C101  23-APR-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E12  075/bct/112    C101  23-JAN-11
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E14  075/bct/176    C103  01-JUN-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E15  075/bct/176    C102  01-JUN-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E18  075/bct/115    C104  01-MAR-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E20  075/bct/166    C101  01-APR-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E30  075/bct/188    C101  23-APR-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E12  075/bct/112    C101  23-JAN-11

    CRN            NAME                 ADDRESS                        PHONE DOB       ENRO CRN            CID   ENROLLDT  COMPLETED
    -------------- -------------------- ------------------------- ---------- --------- ---- -------------- ----- --------- ---------
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E14  075/bct/176    C103  01-JUN-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E15  075/bct/176    C102  01-JUN-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E18  075/bct/115    C104  01-MAR-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E20  075/bct/166    C101  01-APR-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E30  075/bct/188    C101  23-APR-12
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E12  075/bct/112    C101  23-JAN-11
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E14  075/bct/176    C103  01-JUN-12
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E15  075/bct/176    C102  01-JUN-12
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E18  075/bct/115    C104  01-MAR-12

    CRN            NAME                 ADDRESS                        PHONE DOB       ENRO CRN            CID   ENROLLDT  COMPLETED
    -------------- -------------------- ------------------------- ---------- --------- ---- -------------- ----- --------- ---------
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E20  075/bct/166    C101  01-APR-12
    075/bct/154    John                 Jorpati                     51423234 18-DEC-93 E30  075/bct/188    C101  23-APR-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E12  075/bct/112    C101  23-JAN-11
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E13  075/bct/115    C101  23-JAN-11 01-JUN-11
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E14  075/bct/176    C103  01-JUN-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E15  075/bct/176    C102  01-JUN-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E18  075/bct/115    C104  01-MAR-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E20  075/bct/166    C101  01-APR-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E30  075/bct/188    C101  23-APR-12


```

8. Find the natural join of student and enroll.

```sql
    -- Query
    SELECT * FROM STUDENT NATURAL JOIN ENROLL;
    --  Or
    SELECT * FROM STUDENT,ENROLL WHERE STUDENT.CRN = ENROLL.CRN;
    --  Or
    SELECT * FROM STUDENT S,ENROLL E WHERE S.CRN = E.CRN;

    -- Result
        CRN            NAME                 ADDRESS                        PHONE DOB       ENRO CID   ENROLLDT  COMPLETED
    -------------- -------------------- ------------------------- ---------- --------- ---- ----- --------- ---------
    075/bct/112    Anil                 Lalitpur                     9845268 12-JAN-92 E12  C101  23-JAN-11
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E13  C101  23-JAN-11 01-JUN-11
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E14  C103  01-JUN-12
    075/bct/176    Sita                 Lagankhel                   51222765 10-JUN-89 E15  C102  01-JUN-12
    075/bct/115    Bibek                Bhaktapur                   98452688 01-APR-90 E18  C104  01-MAR-12
    075/bct/166    Rohan                New Road                   984548268 12-MAR-92 E20  C101  01-APR-12
    075/bct/188    Puja                 Baneshwor                   42322432 12-JUL-89 E30  C101  23-APR-12


```

9.Find crn, names and enroll date of all students who have taken the course ‘java’.

```sql
    -- Query
    SELECT STUDENT.CRN,STUDENT.NAME,ENROLL.ENROLLDT FROM STUDENT,ENROLL WHERE STUDENT.CRN=ENROLL.CRN
    AND ENROLL.CID = (SELECT COURSEID FROM COURSE WHERE CNAME = 'Java');

    -- Result
    CRN            NAME                 ENROLLDT
    -------------- -------------------- ---------
    075/bct/112    Anil                 23-JAN-11
    075/bct/115    Bibek                23-JAN-11
    075/bct/166    Rohan                01-APR-12
    075/bct/188    Puja                 23-APR-12


```

10.Find the name and address of all the students who are enrolled on 01-jun-2012.

```sql
    -- Query
    SELECT NAME,ADDRESS FROM STUDENT,ENROLL WHERE STUDENT.CRN=ENROLL.CRN AND ENROLL.ENROLLDT ='01-jun-2012';

    -- Result
    NAME                 ADDRESS
    -------------------- -------------------------
    Sita                 Lagankhel
    Sita                 Lagankhel

```

11.Find the names and address of all the students who have taken both course java and
linux.

```sql

    -- SELECT NAME,ADDRESS,CID FROM STUDENT,ENROLL WHERE STUDENT.CRN=ENROLL.CRN AND ENROLL.CID = ;

```
