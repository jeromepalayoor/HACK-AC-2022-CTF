Title: My Little Phony

Description:
```
A little crypto challenge to get you warmed up!

Wrap the plaintext found in ACSI{}, treat "0" as the space character, and ensure that the flag is all uppercase.

Example flag format: ACSI{WELCOME TO THE CTF}

Author: Bennett
```

Given hint: Look at the keypad on your mobile (or Nokia) phone

Given files: [cipher.txt](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Crypto/My%20Little%20Phony/cipher.txt "cipher.txt")

Inside cipher.txt is a string of numbers.

```44335555556660966677755530266304666666305558822255```

This is definitely the kind of nokia phone numberpad letter writing cipher thing. I found its [decoder](https://www.dcode.fr/multitap-abc-cipher).

![image](https://user-images.githubusercontent.com/63996033/199151179-4fe58737-d319-42d1-973f-5d2e3f80b9d3.png)

![image](https://user-images.githubusercontent.com/63996033/199151255-bb7daded-5d62-4340-ad52-6fa65ff85dfa.png)

We got our flag.

Flag: ACSI{HELLO_WORLD_AND_GOOD_LUCK}
