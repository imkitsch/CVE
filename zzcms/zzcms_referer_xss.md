+ version: zzcms2021
+ source: http://www.zzcms.net/about/6.htm
+ issue: xss

# Position
in `ask/caina.php` line 21
![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217180328.png)

The `@$_SERVER['HTTP_REFERER']` can be controlled by the Referer header,and in `showmsg` function
![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217180524.png)

# Poc
`Referer:127.0.0.1";alert('xss');</script>//`
![](https://github.com/imkitsch/CVE/blob/main/zzcms/20220217181126.png)