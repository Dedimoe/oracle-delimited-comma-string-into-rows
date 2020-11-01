# oracle-delimited-comma-string-into-rows
oracle-delimited-comma-string-into-rows

```
SQLPLUS> WITH DATA AS ( 
  SELECT 'aaa,bbb,ccc,ddd,eee,fff,ggg' str FROM dual
)
SELECT trim(regexp_substr(str, '[^,]+', 1, LEVEL)) str
FROM DATA
CONNECT BY instr(str, ',', 1, LEVEL - 1) > 0
```
