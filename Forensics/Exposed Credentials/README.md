Title: Exposed Credentials

Description:
```
We captured some network traffic of some chemistry fan. Give us his username and password so we can login to the same server. We don't know at all how to use this thing/software called "wireshark". Thanks a lot.

Flag Format: ACSI{username_password}

Eg. if the username is "foo" and the password is "bar", the flag is ACSI{foo_bar}

Author: Reyes
```

Given files: [capture.pcapng](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Forensics/Exposed%20Credentials/capture.pcapng "capture.pcapng")

Opening the file in WireShark shows this:

![image](https://user-images.githubusercontent.com/63996033/199071253-61bd7a21-5b54-44e7-895f-7a8945e88055.png)

Lets follow one of the TCP connections as there seems to be many.

![image](https://user-images.githubusercontent.com/63996033/199071638-e05491dc-ca82-491a-b89f-c250617def27.png)
![image](https://user-images.githubusercontent.com/63996033/199071679-9132f2e5-b9b0-4eb9-bf60-b542cd638dd0.png)

Lets change the streams to find anything interesting.

![image](https://user-images.githubusercontent.com/63996033/199071759-a1d3df25-0213-485b-bcee-b874610f8ce9.png)
![image](https://user-images.githubusercontent.com/63996033/199071798-ba501b9c-2b2c-4aea-a243-09bdc60c1f2f.png)

At stream 3 we see what we want. Since the flag is in the format ACSI{username_password}, the username is dihydrogenmonoxide and password is sodiumchloride.

Flag: ACSI{dihydrogenmonoxide_sodiumchloride}
