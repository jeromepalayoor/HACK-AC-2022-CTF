Title: Format String

Description:
```
Format string vulnerabilities are extremely potent in binary exploitation. 
With a simple mistake, an attacker can achieve both arbitrary read and write! 
But this program doesn't allow us to write to any memory region we like, 
so we can't repoint a function call to system('/bin/sh') in the GOT ... Is it unsolvable??

Note that you might need to write a fuzzer for this challenge.

nc alpha.8059blank.ml 3002
nc beta.8059blank.ml 3002

Author: Lucas
```

Given files: [formatstring](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Pwn/Format%20String/formatstring "formatstring") [formatstring.c](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Pwn/Format%20String/formatstring.c "formatstring.c")

Given hints: Your payload will look like this: b'A'*264 + canary + b'A'*8 + ret gadget + win func

Flag: ACSI{h0p3_u_l1k3_1t_uwu_owo}
