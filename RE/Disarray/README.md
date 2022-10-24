Title: Disarray

Description:
```
Can you figure out what the flag is from the piece of code?

Author: Samuel
```

A file was given: https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/RE/Disarray/disarray.c

The file shows this:

```
int main(void){
    char flag[16];
    flag[1] = 'C';
    flag[2] =  'S';
    flag[11] =  '5';
    flag[15] =  '3';
    flag[8] =  'y';
    flag[3] =  'I';
    flag[4] =  '{';
    flag[5] =  'e';
    flag[12] =  '_';
    flag[6] =  '4';
    flag[7] =  '5';
    flag[9] =  '_';
    flag[13] =  '1';
    flag[10] =  '@';
    flag[14] =  '2';
    flag[0] = 'A';
    flag[16] =  '}';
}
```

So the flag is seperated each characted. And it is indexed accordinly.
I used a workaround and removed everything from the file except the flag[i] = chr:

```
    flag[1] = 'C';
    flag[2] =  'S';
    flag[11] =  '5';
    flag[15] =  '3';
    flag[8] =  'y';
    flag[3] =  'I';
    flag[4] =  '{';
    flag[5] =  'e';
    flag[12] =  '_';
    flag[6] =  '4';
    flag[7] =  '5';
    flag[9] =  '_';
    flag[13] =  '1';
    flag[10] =  '@';
    flag[14] =  '2';
    flag[0] = 'A';
    flag[16] =  '}';
```

I added an extra 0 infront of every 1 digit number of the array index.
```
    flag[01] = 'C';
    flag[02] =  'S';
    flag[11] =  '5';
    flag[15] =  '3';
    flag[08] =  'y';
    flag[03] =  'I';
    flag[04] =  '{';
    flag[05] =  'e';
    flag[12] =  '_';
    flag[06] =  '4';
    flag[07] =  '5';
    flag[09] =  '_';
    flag[13] =  '1';
    flag[10] =  '@';
    flag[14] =  '2';
    flag[00] = 'A';
    flag[16] =  '}';
```
Then I uploaded this text into a alphabetizer

![image](https://user-images.githubusercontent.com/63996033/197460657-2f28e70b-b483-44e9-9c03-9d3f85bb5e66.png)

I got this:

```
    flag[00] = 'A';
    flag[01] = 'C';
    flag[02] =  'S';
    flag[03] =  'I';
    flag[04] =  '{';
    flag[05] =  'e';
    flag[06] =  '4';
    flag[07] =  '5';
    flag[08] =  'y';
    flag[09] =  '_';
    flag[10] =  '@';
    flag[11] =  '5';
    flag[12] =  '_';
    flag[13] =  '1';
    flag[14] =  '2';
    flag[15] =  '3';
    flag[16] =  '}';
```
Which gives the flag.

Flag: ACSI{e45y_@5_123}
