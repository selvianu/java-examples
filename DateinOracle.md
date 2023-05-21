##### To insert DATE and System Date in Oracle Table

``` sql
insert into table_name
(date_field)
value
(TO_DATE('2003/05/03 21:02:44', 'yyyy/mm/dd hh24:mi:ss'));
```
``` sql
insert into tasks(id, name, priority, status, assignedto, assigneddate, completeddate) values(1, 'design DB', 'high','pending', 'priya', sysdate,TO_DATE('2023/05/03', 'yyyy/mm/dd'));
```