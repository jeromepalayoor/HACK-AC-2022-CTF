Title: bRocade

Description:
```
CHeck out these Funny Numbers I got from RSALib

Author: Elijah
```

Given files: [funny_numbers.txt](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Crypto/bRocade/funny_numbers.txt "funny_numbers.txt")

Opening the files shows us 3 numbers with the label n, c and e. This is the values for RSA encryption.

![image](https://user-images.githubusercontent.com/63996033/199209231-e5136416-1d74-4134-8496-96bbca986dd2.png)

The description talks about RSALib which has the ROCA vulnarability. When I searched how to decrypt RSA by n, e and c only I got the RsaCtfTool. I will use it.

Install [RsaCtfTool](https://github.com/RsaCtfTool/RsaCtfTool) and run this command to find the flag.

```
python3 RsaCtfTool.py --attack roca -n 6999082965252128742372245818385771615731926505064955771452423777793070673887249072773927720079007269885771058471909582519305239635950041274597486735570703  -e 65537 --uncipher 2303616379857131156764961962764036317371982556098454831208398857900314147638701525135058079613243202542587590154661497564430350685202362225092811302060272
```

The flag is found.
