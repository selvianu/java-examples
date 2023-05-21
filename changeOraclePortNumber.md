```sql
select dbms_xdb.gethttpport as "HTTP-Port",dbms_xdb.getftpport as "FTP-Port
" from dual;
```
```sql
begin
dbms_xdb.sethttpport('80');
end;
/
```