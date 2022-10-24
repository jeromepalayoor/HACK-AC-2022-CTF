Title: Baby RE

Description:
```
Here's an easy RE chall to get warmed up. Have fun!

Author: Bennett
```

Given files: [enc.py](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/RE/Baby%20RE/enc.py "enc.py") and [out.txt](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/RE/Baby%20RE/out.txt "out.txt")

out.txt:
```
606060606060-6060606060606060-80808080-70707070-21212121-90909090909090909090-40404040404040404040-111111-0101010101-5050-1111111111-111111111111-909090909090-505050-1111111111-5050-909090909090-1111111111-5050-505050-40404040404040404040-40404040404040404040-2121-909090909090-90909090909090909090-404040404040404040-404040404040404040-010101010101010101-909090909090-2121-404040404040404040-1111111111111111-909090909090-0101010101010101-11-404040404040404040-11111111111111111111-60606060-212121212121
```
enc.py
```
flag = "[REDACTED]"

arr = []
for ch in flag:
    tmp = str(ord(ch)) #ASCII value of ch as a string
    tmp = tmp.zfill(3) #Pad with "0"
    tmp = tmp[::-1] #Reverse
    arr.append(tmp)

enc = ""
for chunk in arr:
    a = int(chunk[0]) + 1 #a is an int
    b = chunk[1:] #b is a string
    enc += (a * b + "-")
enc = enc[:-1] #Remove trailing dash

print(enc)

```

Since this is a reverse engineering challenge, we need to understand enc.py fully and reverse our way into the flag.

```
flag = "[REDACTED]"  #creates a variable called flag which is encoded in the below alg

arr = [] 
for ch in flag:   #loops through each character
    tmp = str(ord(ch)) #ASCII value of ch as a string   #for example 'A' -> 65
    tmp = tmp.zfill(3) #Pad with "0"    #the zero is padded infront of the number, so 'A' -> '65' -> '065'  this process can be skipped during the reverse process as 065 number is still read as 65 as long as it is in int form, not str
    tmp = tmp[::-1] #Reverse   #reverse the string  so  'A' -> '65' -> '065' -> '560'
    arr.append(tmp)  #add to arr

enc = "" 
for chunk in arr: #loops through each value
    a = int(chunk[0]) + 1 #a is an int  #gets the first number in the value, adds one and stores in 'a'       so 'A' -> '65' -> '065' -> '560' -> 6   (as an integer)
    b = chunk[1:] #b is a string #gets every other number (the next 2 numbers) in the value, stores in 'b'    so 'A' -> '65' -> '065' -> '560' -> '60'  (as a string)
    enc += (a * b + "-") #repeats the 'b' value 'a' times and adds a dash at the end so 'A' -> '65' -> '065' -> '560' -> '606060606060-'
enc = enc[:-1] #Remove trailing dash #removes the last dash

print(enc) #prints the encoded flag as seen in out.txt    so in our example, 'A' which is the first character of the flag, is as 606060606060, which confirms the alg
```

So lets write a reversing script to get our flag

```
enc = "606060606060-6060606060606060-80808080-70707070-21212121-90909090909090909090-40404040404040404040-111111-0101010101-5050-1111111111-111111111111-909090909090-505050-1111111111-5050-909090909090-1111111111-5050-505050-40404040404040404040-40404040404040404040-2121-909090909090-90909090909090909090-404040404040404040-404040404040404040-010101010101010101-909090909090-2121-404040404040404040-1111111111111111-909090909090-0101010101010101-11-404040404040404040-11111111111111111111-60606060-212121212121"
enc_split = enc.split('-') #splits the enc into each encoded character so '6060606606060'
flag = ""  #here shall lie the flag to be decoded
for value in enc_split: 
    a = len(value)//2 - 1   #since the 2 digits are being repeated, just divide 2 minus 1 to get a  so '6060606606060' -> 5
    b = value[0:2]  #since the 2 digits are being repeated, get the first 2 chars    so'6060606606060' -> '60'
    tmp = str(a) + b  #get the tmp in the original code   so '6060606606060' -> '560'
    tmp = tmp[::-1]   #reverse it, now should be a string that is an ASCII number  so '6060606606060' -> '560' -> '065'
    decoded_value = chr(int(tmp))  # get the ascii char   so '6060606606060' -> '560' -> '065' -> 'A'
    flag += decoded_value  #add the char to flag

print(flag) #print flag
```

After running the decoder in cmd, we get the flag:

![image](https://user-images.githubusercontent.com/63996033/197512395-cb175189-b253-4111-830e-bfd77cd6ba01.png)

Flag: ACSI{c1ph3rs_4r3_r3411y_c00l_y0u_kn0w?}
