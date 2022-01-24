# Oracle-Practical-DBMS

## Labs:

1. [LAB 1 : To familiarize with the SQL statements (DML, DDL).](https://github.com/bhimrazy/Oracle-Practical-DBMS/blob/main/Labs/Lab_1.md)
2. [LAB 2 : To familiarize with the SQL Statements (DML: Insert, Update, Delete) and additional functions.](https://github.com/bhimrazy/Oracle-Practical-DBMS/blob/main/Labs/Lab_2.md)
3. [LAB 3 : To familiarize with the SQL statements and the constraints.](https://github.com/bhimrazy/Oracle-Practical-DBMS/blob/main/Labs/Lab_3.md)

## Setup with docker
```bash
    # Link For Oracle Enterprise in docker hub : 
    # Register and checkout here before running pull command.
    # https://hub.docker.com/_/oracle-database-enterprise-edition
    
    # Login Docker
    $ docker login

    # Docker Conatiner : Oracle Enterprise 
    $ docker pull store/oracle/database-enterprise:12.2.0.1-slim 

    # List images
    $ docker images

    # Run container
    $ docker run -d -it store/oracle/database-enterprise:12.2.0.1-slim

    # Connecting from within the container
    $ docker exec -it <container-id> bash -c "source /home/oracle/.bashrc; sqlplus /nolog"

    # Connect to system
    $ connect system
        password : Oradoc_db1

    # Alter session
    $ alter session set "_ORACLE_SCRIPT"=true;  

    # Changing default password for SYS user
    $ alter user sys identified by <new-password>;

```
## Author
- [@bhimrazy](https://www.github.com/bhimrazy)