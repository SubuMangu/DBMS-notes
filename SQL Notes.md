# SQL NOTES
**Creating Table and Displaying**
``` sql
create table emp(
    id integer primary key,
    name varchar(20) not null,
    dob date
);
describe emp
```
**Entering data**
``` sql
insert into emp values (2211100501,'huggendra',DATE '2003-01-01');
insert into emp values (2211100502,'padendra',date '2003-01-02');
insert into emp values (2211100503,'mutendra',date '2003-01-03');
select * from emp --printing the table 
```
**Alter table**
1. Adding column
``` sql
Alter table emp add(
 email varchar(30),
 phone_no varchar(10)
    );
```
2. Modifying data type
``` sql
Alter table emp modify(
 email varchar2(30),
 phone_no integer
    );
```
3. Renaming table
``` sql
Alter table emp rename to employee
-- Renaming table must not be followed by other operations
```
4. Renaming columns
``` sql
Alter table employee rename column
    ph_no to phone_no; 
```
5. Dropping columns
``` sql
Alter table employee drop column phone_no;
Alter table employee drop column email;
```
6. Adding and Removing constraints
``` sql
alter table EMPLOYEES
add Constraint empno_pk primary key(empno);
-- primary key
alter table EMPLOYEES
add Constraint deptid_fk Foreign key(deptid) References departments(deptno);
-- foreign key
```
``` sql
alter table EMPLOYEES
drop Constraint empno_pk;
alter table EMPLOYEES
drop Constraint deptid_pk;
```
**Renaming table**
``` sql
rename employee to emp
```
**Truncate/Deleting all datas inside table**
``` sql
truncate table emp;
select * from emp;
```
<img src="images/Screenshot 2024-06-27 131113.png" width="" height="">\
**Droping table**
``` sql
drop table emp
```
**Constraints**
1. Primary key
``` sql
create table DEPARTMENTS (  
  deptno number,  
  constraint pk_departments primary key (deptno)  
);
``` 
2. Foreign key
``` sql
create table EMPLOYEES (  
  empno number,    
  deptno number,
  constraint pk_employees primary key (empno),  
  constraint fk_employees_deptno foreign key (deptno) 
      references DEPARTMENTS (deptno)  
); 
```
3. Unique key:
``` sql
create table subu(
    id int unique
);
```
- Unique keys can be null, but primary keys cannot be null
4. Composite key
``` sql
create table subu(
 id int,
 name varchar(20),
 constraint pk primary key(id,name));
```
``` sql
insert into subu values (1,'subu');
insert into subu values (1,'Mangu');
select * from subu
```
<img src="images/Screenshot 2024-06-27 163933.png" width="" height="">

``` sql
insert into subu values (1,'subu');
```
output:
ORA-00001: unique constraint (SQL_WXATAWBZXDDAXMLDGNTSADHED.PK) violated ORA-06512: at "SYS.DBMS_SQL", line 1721
``` sql
insert into subu values (null,null);
```
output:ORA-01400: cannot insert NULL into ("SQL_WXATAWBZXDDAXMLDGNTSADHED"."SUBU"."ID") ORA-06512: at "SYS.DBMS_SQL", line 1721

**Select**
- It is used to retrieve the selected data that follow the conditions we want.
1. Selecting columns
``` sql
SELECT Column_Name_1, Column_Name_2, ....., Column_Name_N FROM Table_Name;  
-- Selecting desired columns
SELECT * FROM table_name;  
-- Selecting all columns
```
2. Selecting rows
- Syntax:
``` sql
SELECT * FROM Name_of_Table WHERE [condition];  
```
- example:
``` sql
select * from subu where name='Mangu'  
```
3. Select unique/distinct
``` sql
select unique id from subu
```
``` sql
select distinct id from subu
```
<img src="images/Screenshot 2024-06-27 213055.png" width="" height="">


4. Select Count
- Suppose we have a table named as `sample`\
<img src="images/Screenshot 2024-06-27 214450.png" width="100" height="200">
``` sql
Select count(name) from sample
```
Output:\
<img src="images/Screenshot 2024-06-27 221742.png" width="130" height="">

``` sql
Select count(name) as count_name from sample
```
Output:\
<img src="images/Screenshot 2024-06-27 222015.png" width="130" height="">
``` sql
Select count(*) as count_name from sample
```
<img src="images/Screenshot 2024-06-27 222256.png" width="130" height="">

-We can use condition as given below
``` sql
SELECT COUNT(DISTINCT column_name) FROM table_name WHERE [condition];  
```













