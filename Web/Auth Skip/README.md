Title: Auth Skip

Description:
```
The goal of this warmup/guided challenge is to login as "admin", using SQL Injection!

Go to /tutorial on the website for the guide (if you need to)

Some useful links:

https://portswigger.net/web-security/sql-injection
https://en.wikipedia.org/wiki/SQL_injection

Link: http://alpha.8059blank.ml:4002
Mirror: http://beta.8059blank.ml:4002

Author: Reyes
```

Visiting the website, we will see this:

![image](https://user-images.githubusercontent.com/63996033/197443120-96229493-9aa3-4c58-ba50-5fecce13585e.png)

It is suggested that we use SQL injection.

Lets try username: admin, password: ' OR 1=1 --

![image](https://user-images.githubusercontent.com/63996033/197443415-1e0e4fd9-0373-4ffc-bdd7-44c86799bb27.png)


And we got the flag:

![image](https://user-images.githubusercontent.com/63996033/197443307-385588ec-eb66-4a80-bd29-194a316d6bfc.png)

Flag: ACSI{hehe_ez_sqli_w4rmup}
