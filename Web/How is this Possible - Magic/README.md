Title: How is this Possible - Magic

Description
```
How is this possible? You don't allow a particular password but want the hashes to match?
Sigh there must be some black magic going on here...

Link: http://alpha.8059blank.ml:4001
Mirror: http://beta.8059blank.ml:4001

Author: Reyes
```

Given hint: google "php hash vulnerability"

Visiting the webpage, it shows us the code of the php file of the website.

![image](https://user-images.githubusercontent.com/63996033/197445386-37ee0c20-6aee-446b-8f38-731e0a0a4cb6.png)

By adding, /?pass=RSnake33ncxYMsiIgw at the end of the url, we get this message. This shows that we must perform our exploit in the url.

![image](https://user-images.githubusercontent.com/63996033/197445503-877e55ca-1835-424f-ac5c-836dc88be4c2.png)

Googling "php hash vulnerability", the first result explains in detail what it means.

https://securityaffairs.co/wordpress/36732/hacking/php-hash-comparison-flaw.html

To summarise the vulnerability:
```
hash("sha1", $password) == hash("sha1", $_GET["pass"])
```
in the code is exploitable as hash("sha1", $password) is read as 0-something because the hash starts with 00e. Therefore, we can use another unhashed text, that gives a hash that starts with '0e', and
![image](https://user-images.githubusercontent.com/63996033/197445942-583bee02-4806-4be7-83df-6b17de387e63.png)

After researching for a while, I found this list of possible texts and its hashes that will work.
https://github.com/spaze/hashes/blob/master/sha1.md

By using any one of the text, in this case i used 'aaroZmOk', the flag is found:

![image](https://user-images.githubusercontent.com/63996033/197446489-74b23bdd-66da-456c-992f-8a6e47a46cc0.png)

Flag: ACSI{un0r1gin4l_ch4llang3s_ar3_wh4t_1_am_b35t_at}
