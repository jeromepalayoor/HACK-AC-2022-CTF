Title: Serial Killer

Description

```
Analyse the data and obtain the flag.

Author: Samuel
```

Given file: [serial_killer.sal](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Misc/Serial%20Killer/serial_killer.sal "serial_killer.sal")

I quickly serched up which application can open .sal files but could not find anything. Search the word 'ctf' together with it to get better results. 
I found [this write up](https://ctftime.org/writeup/27682) which shows a similar challenge and the application used to open .sal files. It is [Logic Analyzer Saleas](https://www.saleae.com/downloads/). Download it. And open the file in it.

![image](https://user-images.githubusercontent.com/63996033/197684179-14be91d2-a162-441b-8d0b-1ca2cc040f7f.png)

Here we can see that there is information in channel 0. But to get it we need to use the analyser. Select Async Serial. Make sure Channel 0 is selected. Go to terminal.

![image](https://user-images.githubusercontent.com/63996033/197684258-e085f93d-b29d-4f75-a60c-f28c01a47a02.png)
![image](https://user-images.githubusercontent.com/63996033/197684316-49a476b4-1740-420b-b5a9-d5bd8d1d5286.png)
![image](https://user-images.githubusercontent.com/63996033/197684332-944fa82d-4a2a-438d-8829-1016a4e12064.png)
![image](https://user-images.githubusercontent.com/63996033/197684441-209674f6-e9a0-4198-a361-593e100c883c.png)
![image](https://user-images.githubusercontent.com/63996033/197684449-11b12cc8-3267-4f89-b963-8b217bebc434.png)

To get our flag we need to change our bit rate to the correct one. We can try brute force all the common bit rates which can be found [here](https://en.wikipedia.org/wiki/Serial_port#Settings).

![image](https://user-images.githubusercontent.com/63996033/197684679-52f65b42-3022-40cb-b134-8e9ffc986330.png)
![image](https://user-images.githubusercontent.com/63996033/197685176-67ea3bac-ea26-4d66-82d4-9a90d3b7dbf0.png)
![image](https://user-images.githubusercontent.com/63996033/197684803-df5c0d12-cf31-48e0-93d0-0cf8f6942051.png)

After trying for a while, 9600 was the working bitrate, which allowed us to get the flag.

Flag: ACSI{l0g1c_4n4lyz3r_101}
