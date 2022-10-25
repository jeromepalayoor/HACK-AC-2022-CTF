Title: Banana Overflow

Description:

```
Just read about this thing called "Integer Overflow", I wonder if it's dangerous?
I've set up a banana-money-printing machine to test this out.

nc alpha.8059blank.ml 3003
nc beta.8059blank.ml 3003

Author: Lucas
```

Given files: [banana](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Pwn/Banana%20Overflow/banana "banana") [banana.c](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Pwn/Banana%20Overflow/banana.c "banana.c")

Given hint: Perhaps you can find a way to donate so much that you start earning money?

This challenge obviously requires us to do integer overflow to the C program.

banana.c shows us this: It does not allow negative numbers, which includes numbers greater than the integer overflow in C.
To get the flag, the balance needs to be larger than 1000000000.

```
# include <stdio.h>

int main() {
    int balance = 1;
    int donate;
    while (balance < 1000000000) {
        puts("Please enter in how much you want to donate (don't worry, money is free!)")
        scanf("%d", &donate);
        if (donate <= 0) {
            puts("Why you so stingy");
            return 0;
        }
        balance -= donate;
        printf("You currently have: $%d\n\n", balance);
    }
    system("cat flag.txt");
}

```

The number for integer oveflow in C is 2147483647. I used netcat to access the program and it showed me this. 

![image](https://user-images.githubusercontent.com/63996033/197679987-7dbfcefb-683f-4383-98ea-9622a57919f7.png)
![image](https://user-images.githubusercontent.com/63996033/197680303-0f81de1c-d506-49ba-849e-96ac7534a174.png)

Lets now try a number bigger than 2147483647. 

![image](https://user-images.githubusercontent.com/63996033/197680385-9d14c016-af7d-4769-b697-6660f3216969.png)

Oops. What about a number less than 2147483647?

![image](https://user-images.githubusercontent.com/63996033/197680448-6aff2375-ce35-413a-b1c5-2e35509a7a42.png)

There we go!

Flag: ACSI{w4w_i_jus7_h4ck3d_0cbc}
