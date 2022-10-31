Title: Memdump Part 1

Description:
```
Could you find what website was visited?
There is a plugin for volatility that will allow us to extract chrome history .
Perhaps it might give us something useful...

Wrap the string you find with the ACSI{...} flag format.

Author: Samuel
```

[Volatility](https://www.volatilityfoundation.org/releases)

[Volatility Cheat Sheet](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-examples) 

[Google drive mirror](https://drive.google.com/file/d/1Z0m-83Cmt2eY0Zh_XoiTIDWXycDjBx2k/view?usp=sharing)

After downloading the file, I immediately checked for any possible strings I could find by using ~~notepad~~ HxD editor (the file is too big for notepad to read but is fine in HxD editor. 

![image](https://user-images.githubusercontent.com/63996033/199074782-29f173fc-5cc6-4649-9f03-7b25214f2354.png)

Nope. That's the flag for part 2. Some hints suggest that the website is pastebin.com. Let's try that. 

![image](https://user-images.githubusercontent.com/63996033/199074977-57340744-b93a-4a34-ac51-c3fcb394e054.png)
![image](https://user-images.githubusercontent.com/63996033/199074999-9a9b091b-ab43-48c7-b783-f0038ec29fe3.png)
![image](https://user-images.githubusercontent.com/63996033/199075048-4644725f-ef6a-4f91-8dfb-e07c9ae1d5e7.png)

This 3rd result seems sus. Lets check it out. [https://pastebin.com/iC9nKd3s](https://pastebin.com/iC9nKd3s "https://pastebin.com/iC9nKd3s")

![image](https://user-images.githubusercontent.com/63996033/199075289-57f4b927-8da3-4300-a0c6-cfa6c60de6d3.png)

We got our flag.

Flag: ACSI{i_can_see_your_history}
