``` sql create table emp(id number primary key, name varchar2(50) unique not null, email varchar2(50) unique,designation varchar2(30) not null);
insert into emp (id, name, email,designation) values(102, 'Abi', 'abi@gmail.com','trainee');
```
```sql
select * from emp;
```
``` sql 
create table tasks(id number primary key, 
name varchar2(50) not null, priority varchar(20) not null, 
status varchar(20) not null, 
assignedTo varchar(30) not null, assignedDate date not null, 
completedDate date not null, CONSTRAINT task_user
    FOREIGN KEY (assignedTo)
    REFERENCES emp (name));
```
``` sql
drop table tasks;
```
``` sql 
select * from tasks;
```
``` sql
insert into tasks(id, name, priority, status, assignedto, assigneddate, completeddate) 
values(1, 'design DB', 'high','pending', 'priya', sysdate,TO_DATE('2023/05/03', 'yyyy/mm/dd'));
insert into tasks(id, name, priority, status, assignedto, assigneddate, completeddate) 
values(2, 'design DB', 'high','pending', 'Abi', sysdate,TO_DATE('2023/05/03', 'yyyy/mm/dd'));
```
