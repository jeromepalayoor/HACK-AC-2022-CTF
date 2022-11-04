Title: Memdump Part 2

Description:
```
Help me find what was typed in notepad! Start off by analysing running processes.

Author: Samuel
```

[Volatility](https://www.volatilityfoundation.org/releases)

[Volatility Cheat Sheet](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-examples) 

[Google drive mirror](https://drive.google.com/file/d/1Z0m-83Cmt2eY0Zh_XoiTIDWXycDjBx2k/view?usp=sharing)

After downloading the file, I immediately checked for any possible strings I could find by using ~~notepad~~ HxD editor (the file is too big for notepad to read but is fine in HxD editor).

![image](https://user-images.githubusercontent.com/63996033/199073929-de0da600-6120-4fec-9887-747fc9bfe3d5.png)

It looks like gibberish. Lets search for the file format 'ACSI{' and click 'Search All'.

![image](https://user-images.githubusercontent.com/63996033/199074057-d2bb121a-9f82-43d4-bdc7-dacbfc74827b.png)
![image](https://user-images.githubusercontent.com/63996033/199074130-aa4f8d06-e303-41ff-947a-d98190e5c5b5.png)

Oops, we just found our flag for this part. Nice!

Flag: ACSI{notepad_task_failed_successfully}
