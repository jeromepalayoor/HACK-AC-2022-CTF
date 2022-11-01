Title: Poetry moves

Description:
```
XOR is like poetry.

Well it's not, but I XORed a poem by accident. I don't remember the key, but it was 5 bytes long. Can you help me retrieve it?

Author: I-En
```

Given files: [poem.txt](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Crypto/Poetry%20moves/poem.txt "poem.txt")

Opening poem.txt shows a string of random characters.

![image](https://user-images.githubusercontent.com/63996033/199151553-37bc4e41-56ba-4222-ab71-13690aeb444b.png)

I will use [this](https://www.dcode.fr/xor-cipher) XOR decoder. Make sure to select the key size as 5 bytes.

![image](https://user-images.githubusercontent.com/63996033/199151781-21b8b7ad-4b53-4671-b65f-db42da693151.png)

![image](https://user-images.githubusercontent.com/63996033/199151787-866d4522-349c-4acd-9158-32a7d58f752b.png)

Copy this key and paste it back into the decrypter as the key in hex.

![image](https://user-images.githubusercontent.com/63996033/199151857-5510fc32-d336-4f96-a490-4136b28ef04a.png)

![image](https://user-images.githubusercontent.com/63996033/199151879-946e4083-57fb-40e6-8cc1-aa46640f9f67.png)

This gives us the flag.

Flag: ACSI{x_0r_Sh4ke_sp34r}
