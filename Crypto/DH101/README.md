Title: DH101

Description:
```
Follow the guide, and try to learn something along the way.

Link: http://alpha.8059blank.ml:4006
Mirror: http://beta.8059blank.ml:4006

Author: Samuel
```

Visiting the website shows us a cryptography tutorial on DIFFIE-HELLMAN KEY EXCHANGE.

![image](https://user-images.githubusercontent.com/63996033/199206633-6f278081-9fc8-47c7-8292-69ac35a2d7c3.png)

![image](https://user-images.githubusercontent.com/63996033/199206682-746b7b91-fcca-4321-b43b-0fe069649330.png)

Going to workshop 1, it shows us how to do it. Workshop 2 is what we need to solve to get the flag.

![image](https://user-images.githubusercontent.com/63996033/199206837-4813caae-ab54-4c49-8b42-12096bc2defd.png)

Workshop shows us a link to calculate numbers we need. Let's open that in another tab. We need to find a and b.

As seen in the tutorial, g is the base, p is the modulus and g^a and g^b is the powers for a and b respectively.

![image](https://user-images.githubusercontent.com/63996033/199207603-bad93f7e-e053-485c-a005-e7db40353887.png)

We need to put in g^a in the power to get a, and g^b for b. The values for a and b are very big.

![image](https://user-images.githubusercontent.com/63996033/199207786-b7c5938b-fa9b-4b84-b516-23f37ece89c6.png)
![image](https://user-images.githubusercontent.com/63996033/199207870-3737ac15-cba6-4e39-8236-bfc0aaab1493.png)

Let's open up python to get our flag.

![image](https://user-images.githubusercontent.com/63996033/199207934-7cccadc5-b775-4262-87cb-476265db637c.png)

Remove the spaces in the number and input the correct values into python:

![image](https://user-images.githubusercontent.com/63996033/199208313-56517654-8e5b-4678-9223-3fc5344f9c59.png)

Flag: ACSI{1556040610615615377229749149768935688558250674767}
