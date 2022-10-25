Title: Sanity Check

Description:

```
Welcome to HACK@AC 2022!

Flag: ACSI{w3lc0m3_t0_h4ckac_2022}
```

Given hint: I'm losing my sanity...

Hmm... This seems like a hard challenge!

The given 'flag' seems to be encrypted.

Let's try to use ROT-13 decoder from [here](https://www.dcode.fr/rot-13-cipher) to deocde it.

![image](https://user-images.githubusercontent.com/63996033/197681159-7578c0df-6f4e-4823-bc02-123eba72e2b8.png)

It seems like NPFV{j3yp0z3_g0_u4pxnp_2022} is double encoded. Maybe let's try with Caesar Cipher decoder from [here](https://www.dcode.fr/caesar-cipher).

![image](https://user-images.githubusercontent.com/63996033/197681346-e090d3d3-877a-497f-861b-3d91509d128a.png)
![image](https://user-images.githubusercontent.com/63996033/197681395-629e23bf-901f-418f-8ed1-0b94d4e38e40.png)

It looks like we got our flag.

Flag: ACSI{w3lc0m3_t0_h4ckac_2022}
